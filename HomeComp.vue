 <template>
   <div>
     <div v-if="isAuthenticated">
      <div>Welcome <b>{{ username }}</b></div>
       
       <button @click="logout">Logout</button>
      </div>

       <div v-else>
     <label>Your name</label>
     <input v-model="username" @keyup.enter="login" />
    <button @click="login"></button>
    </div>
   </div>
 </template>

<script>
export default{
    name:'HomePage',
    data(){
        return{
            isAuthenticated: false,
            username:''
        }
    },
    methods: {
        login(){
            if(this.username !== ''){
                console.log('You entered as',this.username)
                this.isAuthenticated = true
                localStorage.setItem('isAuthenticated', true)
                localStorage.setItem('username', this.username)
                this.$router.push({
                    name: 'Chat',
                    queru:{username: this.username}
                })
            }else{
console.log('Please ,enter your name')
            }
        },
        logout(){
            this.isAuthenticated = false
            this.username = ''
            localStorage.removeItem('isAuthenticated')
            localStorage.removeItem('username')
        }

        },
   
    created(){
        if(localStorage.getItem('isAuthentcated')){
            this.isAuthenticated = true
            this.username = localStorage.getItem('username')
        } } }
//}

</script>


<style scoped>
div{
    padding: 20px;
    font-size: 25px;
}

label{
    margin: 1px;
    
}

button{
    margin-left: 10px;

}
</style>