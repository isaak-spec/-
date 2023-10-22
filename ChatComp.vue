<template>
<div v-if="username">
    <div class="chat">
        <h3>Chat</h3>
        <div class="text" v-for="message in message" :key="message.id">
{{ message.username }}:{{message.text  }}
        </div>
        <div v-show="emptyMsg" class="empty">
             No messages

        </div>
    </div>
    <input v-model="newMessage" placeholder="Texst your message">
    <button @click="sendMessage" @keyup.enter="sendMessage">Send</button>
    <button v-show="deleteBtn" @click="delMessage">Delete</button>

</div>
<div v-else class="alert">
    For auth go to   <router-link :to="{name:Home}">Link</router-link>

</div>


</template>


<script>
import { computed } from 'vue';

export default{
name:'ChatPage',
data(){
    return{
        messages:[],
        newMessage:'',
        emptyMsg: true,
        deleteBtn: false,
        username: localStorage.getItem('username')
    }
    },
    computed(){
        localStorage.setItem('username',this.$route.query.username)
    },
    methods:{
sendMessage(){
    if(!this.username){
        this.username = 'Anonim'
    }
    if(this.newMessage !== ''){
        this.emptyMsg = false
        console.log('You entered message:',this.newMessage)
        this.message.push(
            {
                id:new Date ().getTime(),
                text: this.newMessage,
                user: this.username
            }
        )
        this.saveChatRecords()
        this.newMessage=''
        this.defaulteBtm = true
    }else{
        console.log('Please enter message')
        alert('Please enter message')
    }
},
delMessage(){
    this.messages = []
    localStorage.removeItem('messges_${this.username}', JSON.stringify(this.message))
    console.log('All messages deleted')
    this.emptyMsg = true
},
saveChatRecords(){
    const records = this.message
    console.log(records)
    localStorage.setItem('messages_${this.username}',JSON.stringify(records))
},


loagChatRecords () {
    const records = JSON.parse(localStorage.getItem(`messages_${this.username}`))
    if(records){
        this.message = records
        this.emptyMsg = false
    }
}



    },
    created(){
        this.LoagChatRecords()
    }
}


</script>

<style>
.h2{
    color: honeydew;
    height: 100%;
    border: 5px;
    background-color: blanchedalmond;
    color: black;
    font-weight: 20px;
    margin: 20px;
    padding: 15px;
}
.empty{
margin-bottom: 30px;
font-style: italic;
}

.input{
    margin-right: 15px;

}

.putton{
    margin-left: 5px;
    margin-bottom: 20px;
}




.alert{
    padding: 30px;
}
</style>
