<template>
    <main>
        <div class="leftpan">
            <img src="../assets/cover.png" alt="Logo">
            <nav>
                <ul>
                    <li><a href="#">Home</a></li>
                    <li><a href="#">Statistic</a></li>
                    <li><a href="#">Contact</a></li>
                </ul>
            </nav>
        </div>
        <div class="rightspan">
            <div class="user">
                <Icon icon="charm:menu-hamburger" width="24" :inline="true" class="toggle" />
                <span>
                    <Icon icon="carbon:user-avatar-filled-alt" width="30" :inline="true" />
                    {{username}} <button @click="logout()">Logout</button>
                </span>
            </div>
            <div style="width: 100%; padding: 1rem; 1rem; background: #ccc"></div>
            <div class="dataSection">
                <div class="balance-wrapper" title="Uchenna' acc. balance">
                    <h2>200,000.00</h2>
                    <small>
                        Acc. Balance
                        <Icon icon="ant-design:info-circle-outlined" :inline="true" />
                    </small>
                </div>
                <div class="balance-wrapper">
                    <h2>Acc. balance:</h2><small>200,000.00</small>only
                </div>
                <div class="balance-wrapper">
                    <h2>Acc. balance:</h2><small>200,000.00</small>only
                </div>
            </div>

            <div class="table-wrap">
                <table>
                    <tr>
                        <th>Name</th>
                        <th>Acc. balance</th>
                        <th colspan="3">Operation</th>
                    </tr>
                    <tr>
                        <td>Uchenna Anya</td>
                        <td>1000,000.00</td>
                        <td><button>Deposit</button></td>
                        <td><button>Withdraw</button></td>
                        <td><button>Transfer</button></td>
                    </tr>
                </table>
            </div>
            <footer>Uchenna Anya &copy;</footer>
        </div>
    </main>
</template>

<script>
import { Icon } from '@iconify/vue';

export default {
    name : 'UserDashboard',
     components: {
		Icon,
	},
    data() {
        return {
            username : localStorage.getItem('username'),
        }
    },
    mounted(){
        // if (localStorage.getItem('username') == null || localStorage.getItem('username')==""){
        //     alert("Please Login to continue")
        //     this.$router.push('/')
        // }
        const config = {
            headers: {
                'Content-Type': 'application/x-www-form-urlencoded'
            }
        }
        const userId ={
            userId:1
        }
        this.axios.post(this.$baseUrl+'get-info', userId, config).then((response) => {
            console.log(response.data)
        })
        this.axios.post(this.$baseUrl+'user-orders', userId, config).then((response) => {
            console.log(response.data)
        })
    },


    methods: {
        logout() {
            localStorage.removeItem('username');
            localStorage.clear()
            this.$router.push('/')
        },
        toggle(){
        },
    },
}
</script>


<style scoped>
.leftpan {
    height: 100vh;
    width: auto;
    border-right: 1px solid ;
    padding-right: 1rem;
    display: none;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
}

.leftpan li, a {
    list-style: none;
    text-decoration: none;
    padding: 0.4rem;
}

.leftpan img {
    display: block;
    height: 10vh;
}

main {
    justify-content: space-between;
}
.table-wrap {
width: 90%;
overflow: auto;
}

tr:nth-child(odd) {
    background: #ccc;
}

table {
  border-collapse: collapse;
  width: auto;
margin: auto;
}
th, td {
  padding: 0.25rem;
  text-align: left;
  border: 1px solid #ccc;
}
tbody tr:nth-child(odd) {
  background: #eee;
}
.dataSection {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

.balance-wrapper {
    box-shadow: 2px 1px 9px 0 #ccc;
    padding: 2rem;
    border-radius: 5px;
    margin: 1rem;
    transition: all 0.5s ease;
    /* background-image: linear-gradient(to right, rgba(125, 181, 130, 0.5)) !important; */
    background-image: linear-gradient(to bottom right, rgb(255, 255, 255) , rgb(176, 176, 219))
}
.balance-wrapper small {
    display: flex;
    justify-content: space-between;
}
.rightspan {
    display: flex;
    flex-direction: column;
    /* justify-content: space-between; */
    padding-bottom: 1rem 1rem 0 0;
    align-items: center;
}
.rightspan .user {
    text-align: right;
    box-shadow: 0 0 5px 0 #ccc;
    width: 100vw;
    display: flex;
    justify-content: space-between;
    padding: 1rem;
}

.user span {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.balance-wrapper:hover {
    transform: scale(1.1);
    cursor: pointer;
}
.rightspan button {
    padding: 0.4rem 1rem;
    border: none;
    transition: all 0.5s ease;
}

.rightspan button:hover {
    transform: scale(1.1);
    cursor: pointer;
}

footer {
    background: #ccc;
    width: 88.5vw;
    text-align: right;
    padding: 1rem;
    display: none;
    position: absolute;
    bottom: 0;
    left: 11.3vw;
}

@media only screen and (min-width: 768px) {
    .rightspan .user {
        justify-content: end;
        align-items: center;
        width: 88.5vw;
    }
    .toggle {
        display: none;
    }
    .dataSection {
    flex-direction: row;
  }

  .balance-wrapper {
    margin: 3rem;
  }

  .leftpan {
      width: 10vw;
      display: inline-block;
      display: flex;
  }
  main {
    padding: 0 1rem;
    display: flex;
  }

  footer {
      display: block;
  }
  }
</style>>