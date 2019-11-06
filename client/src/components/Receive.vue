<template>
    <div>
        <div v-for="(notification, index) in notifications" :key="index">
            {{notification.title + " - " + notification.type}}
            <br>
            {{notification.message}}
        </div>
    </div>
</template>

<script>
export default {
    name: 'Receive',
    methods: {
    },
    data() {
        return {
            notifications: []
        }
    },
    mounted() {

    },
    sockets: {
        connect() {
            console.log("Socket connected : receive")
        },
        nice: function(data) {
            console.log(data)
            this.notifications.push(data)
        }

    },
}
</script>