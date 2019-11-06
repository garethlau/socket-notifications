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
            Type<br>
            <select v-model="type">
                <option>Food</option>
                <option>Workshop</option>
                <option>Event</option>
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
            type: null,
        }
    },
    methods: {
        notify () {
            console.log("NOTIFY")
            let d = {
                title: this.title,
                message: this.message,
                type: this.type
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
