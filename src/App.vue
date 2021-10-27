<template>
    <div id="app">
      <div class="container">

      </div>
    </div>
</template>

<script>
import Echo from "laravel-echo";
import socketio from "socket.io-client";

// import io from 'socket.io-client'

export default {
    name: "App",

    data() {
        return {
            Echo: null,
            token: null,
            accNo:null
        };
    },
    created() {
        this.Echo = new Echo({
            broadcaster: "socket.io",
            client: socketio,
            host: window.location.hostname + ":6001",
            // auth: {
            //     headers: {
            //         Authorization: `Bearer ${this.token}`,
            //     },
            // },
        });

        this.Echo.channel("ice_channel").listen("IceEvent", (e) => {
            console.log(e);
        });
        // this.echo
        //     .private(`user${this.accNo}`)
        //     .listen(".qrcodepayment", (data) => {
        //         console.log("dattttttta", data);
        //     });
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
