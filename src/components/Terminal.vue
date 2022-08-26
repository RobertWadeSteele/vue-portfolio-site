<template>
<div id="terminal"></div>
</template>

<script setup>
import $ from 'jquery';
import terminal from 'jquery.terminal';
import router from '@/router/index';

$(function() {
    $('#terminal').terminal(function(command) {
        var cmd = $.terminal.parse_command(command);
        if (cmd.name === 'ls') {
            var files = router.getRoutes()
            console.log(locale);
        } else if (cmd.name === 'echo') {
            this.echo(cmd.rest);
        } else if (cmd.name === '') {
            return;
        } else if (cmd.name === 'clear') {
            this.clear();
            this.echo(terminalName());
        } else {
            this.echo('That\'s not allowed! (╯°□°)╯︵ ┻━┻');
        }
    }, {
        greetings: terminalName,
        clear: false
    });
})

function terminalName () {
    return "     ____        __              __     _____ __            __   \n    / __ \\____  / /_  ___  _____/ /_   / ___// /____  ___  / /__ \n   / /_/ / __ \\/ __ \\/ _ \\/ ___/ __/   \\__ \\/ __/ _ \\/ _ \\/ / _ \\\n  / _, _/ /_/ / /_/ /  __/ /  / /_    ___/ / /_/  __/  __/ /  __/\n /_/ |_|\\____/_.___/\\___/_/   \\__/   /____/\\__/\\___/\\___/_/\\___/ \n                                                                \nGot here by mistake? Type \"exit\" or click the x at the top right.\nType \"help\" for a list of commands."
}
</script>

<style lang="scss">
@import url("https://unpkg.com/jquery.terminal/css/jquery.terminal.min.css");

#terminal {
    width: 90%;
    height: 60vh;
    margin-left: auto;
    margin-right: auto;
    text-align: left;
    border-radius: 15px;
}
</style>