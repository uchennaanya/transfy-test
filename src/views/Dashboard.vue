<template>
    <main>
        <div class="leftpan">
            <img src="../assets/cover.png" alt="Logo">
            <nav>
                <ul>
                    <li><a href="#">Username</a></li>
                    <li><a href="#">Statistic</a></li>
                    <li><a href="#">Contact</a></li>
                    <li><a href="#">Logout</a></li>
                </ul>
            </nav>
        </div>
        <div class="rightspan">
            <div class="user">
            {{username}} <button @click="logout()">Logout</button>
            </div>
            <div class="dataSection">
                <div class="balance-wrapper">
                    <h2>Acc. balance:</h2><small>200,000.00</small>only
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

export default {
    name : 'UserDashboard',
    data() {
        return {
            username : localStorage.getItem('username')
        }
    },
    mounted(){
        if (localStorage.getItem('username') == null || localStorage.getItem('username')==""){
            alert("Please Login to continue")
            this.$router.push('/')
        }
    },
    methods: {
        logout() {
            localStorage.removeItem('username');
            localStorage.clear()
            this.$router.push('/')
        }
    }

}
</script>


<style scoped>
.leftpan {
    height: 100vh;
    width: 10vw;
    border-right: 1px solid ;
    display: inline-block;
    padding-right: 1rem;
    display: flex;
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
    height: 6vh;
}

main {
    display: flex;
    justify-content: space-between;
    padding: 0 1rem;
}

.table-wrap {
display: flex;
justify-content: center;
}

tr:nth-child(odd) {
    background: #ccc;
}

tr {
    padding: 2rem !important;
}


table, th, td {
  border: none;
  border-collapse: collapse;
}
.rightspan {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    padding-bottom: 1rem 1rem 0 0;
    align-items: center;
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
    margin: 3rem;
}
.rightspan button {
    padding: 0.4rem 1rem;
    border: none;
    transition: all 0.5s ease;
}

.rightspan button:hover {
    transform: scale(1.1);
}

.rightspan .user {
    text-align: right;
    box-shadow: 0 0 5px 0 #ccc;
    width: 90vw;
    padding: 1rem;
}

footer {
    background: #ccc;
    width: 90vw;
    text-align: right;
    padding: 1rem;
}

@media only screen and (min-width: 768px) {
    .dataSection {
flex-direction: row;
  }

  .balance-wrapper {
margin: 1rem;
  }
  }
</style>>