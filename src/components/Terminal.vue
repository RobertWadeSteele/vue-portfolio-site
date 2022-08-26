<template>
<div id="draggable-terminal"><div id="terminal"></div></div>
</template>

<script setup>
import $ from 'jquery';
import terminal from 'jquery.terminal';
import router from '@/router/index';
import { onMounted } from 'vue';

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

// ######################333

onMounted(() => {
    dragElement(document.getElementById("draggable-terminal"));
})

function dragElement(elmnt) {
  var pos1 = 0, pos2 = 0, pos3 = 0, pos4 = 0;
  if (document.getElementById(elmnt.id + "header")) {
    // if present, the header is where you move the DIV from:
    document.getElementById(elmnt.id + "header").onmousedown = dragMouseDown;
  } else {
    // otherwise, move the DIV from anywhere inside the DIV:
    elmnt.onmousedown = dragMouseDown;
  }

  function dragMouseDown(e) {
    e = e || window.event;
    e.preventDefault();
    // get the mouse cursor position at startup:
    pos3 = e.clientX;
    pos4 = e.clientY;
    document.onmouseup = closeDragElement;
    // call a function whenever the cursor moves:
    document.onmousemove = elementDrag;
  }

  function elementDrag(e) {
    e = e || window.event;
    e.preventDefault();
    // calculate the new cursor position:
    pos1 = pos3 - e.clientX;
    pos2 = pos4 - e.clientY;
    pos3 = e.clientX;
    pos4 = e.clientY;
    // set the element's new position:
    elmnt.style.top = (elmnt.offsetTop - pos2) + "px";
    elmnt.style.left = (elmnt.offsetLeft - pos1) + "px";
  }

  function closeDragElement() {
    // stop moving when mouse button is released:
    document.onmouseup = null;
    document.onmousemove = null;
  }
}
</script>

<style lang="scss">
@import url("https://unpkg.com/jquery.terminal/css/jquery.terminal.min.css");

#terminal {
    width: 70vw;
    height: 60vh;
    // position: absolute;
    // margin-left: auto;
    // margin-right: auto;
    text-align: left;
    border-bottom-left-radius: 15px;
    border-bottom-right-radius: 15px;
    margin-top: 2em;
}

#draggable-terminal {
    top: 0;
    left: 0;
    position: absolute;
    background-color: gray;
    border-radius: 15px;
}
</style>