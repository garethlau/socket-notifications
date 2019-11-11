<template>
    <div>
        Send
        <p>
            Title<br>
            <input type="text" v-model="title"/>
        </p>
        <p>
            Message<br>
            <input type="text" v-model="message"/>
        </p>
        <p>
            Date<br>
            <input type="text" v-model="date"/>
        </p>
        <p>
            Type<br>
            <select v-model="type">
                <option>food</option>
                <option>workshop</option>
                <option>event</option>
                <option>travel</option>
            </select>
        </p>
        <button @click="notify">Send</button>
    </div>

</template>
<script>
export default {
    name: "Send",
    data () {
        return {
            title: "",
            message: "",
            date: "",
            type: null,
        }
    },
    methods: {
        notify () {
            console.log("NOTIFY")
            let d = {
                title: this.title,
                body: this.message,
                category: this.type,
                date: this.date,
                sortDate: new Date().toUTCString()
            }
            console.log(d);
            this.$socket.emit("notify", d)    
        }
    },
    mounted() {
        
    },
    sockets: {
        connect() {
            console.log("Socket connected")
        }
    }
}
</script>
