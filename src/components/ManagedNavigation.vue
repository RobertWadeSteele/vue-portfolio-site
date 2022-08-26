<template>
<div id="nav-selection">
    <input id="terminal-toggle" type="checkbox" />
    <div id="terminal-toggle-container">
        <label id="terminal-toggle-label" for="terminal-toggle">Prefer a terminal?</label>
        <label id="terminal-toggle-icon" for="terminal-toggle"></label>
        <Terminal/>
    </div>
    <NavBar />
</div>
</template>

<script setup>
import NavBar from '@/components/NavBar.vue';
import Terminal from '@/components/Terminal.vue';
</script>

<style lang="scss">
#terminal-toggle-container {
    position: absolute;
    padding-top: 1em;
    padding-left: 1em;
    display: flex;
    justify-content: center;
    align-items: center;
}

#terminal-toggle-label {
    color: white;
    font-size: 0.9em;
}

#terminal-toggle {
    display: none;
}

#terminal-toggle-icon {
    display: inline-block;
    width: 0.8em;
    height: 0.8em;
    background-color: white;
    border-radius: 50%;
    margin-left: .5em
}

#terminal-toggle:checked ~ #terminal-toggle-icon {
    background-color: lime;
}

#terminal {
    display: none;
}

#terminal-toggle:checked ~ #terminal-toggle-container #terminal {
    display: block;
}

#terminal-toggle:checked ~ #nav-bar {
    display: none;
}

@media only screen and (max-width: 700px) {
    #terminal-toggle-container {
        display: none;
    }

    #terminal {
        display: none;
    }
}
</style>