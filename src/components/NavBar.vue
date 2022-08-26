<template lang="html5">
    <div id="nav-bar">
        <input id="menu-toggle" type="checkbox" />
        <div id="cover">
            <label class="menu-button-container" for="menu-toggle">
                <div class="menu-button"></div>
            </label>
            <nav id="menu">
                <router-link class="nav-link" to="/">Home</router-link>
                <router-link class="nav-link" to="/gallery">Gallery</router-link>
                <router-link class="nav-link" to="/terminal">Terminal</router-link>
                <router-link class="nav-link" to="/about">About</router-link>
            </nav>
        </div>
    </div>
</template>

<script setup>

</script>

<style scoped lang="scss">
@import '@/scss/dark-colors.scss';

.nav-link {
    text-decoration: none;
    padding: 1em;
    display: block;
    color: $link-color;
    background-color: $primary-color;
}

/* ###################################### */

#menu {
    overflow: hidden;
}

#menu-toggle {
    display: none;
}

.menu-button-container {
    display: none;
}

.menu-button,
.menu-button::before,
.menu-button::after {
    display: block;
    background-color: #fff;
    // position: absolute;
    height: 4px;
    width: 30px;
    transition: transform 400ms cubic-bezier(0.23, 1, 0.32, 1);
    border-radius: 2px;
}

.menu-button::before {
    content: '';
    margin-top: -8px;
}

.menu-button::after {
    content: '';
    margin-top: 12px;
}

#menu-toggle:checked + .menu-button-container .menu-button {
    background: rgba(255, 255, 255, 0);
}

#menu-toggle:checked + .menu-button-container .menu-button::before {
    margin-top: 0px;
    transform: rotate(405deg);
}

#menu-toggle:checked + .menu-button-container .menu-button::after {
    margin-top: -4px;
    transform: rotate(-405deg);
}

.nav-link {
    display: inline-block;
    margin-top: 2px;
    &::after {
        content: '';
        display: block;
        width: 0;
        height: 2px;
        background: $link-color;
        transition: width .3s;
    }

    &:hover::after {
        width: 100%;
        transition: width .3s;
    }
}

/* ###################################### */

@media only screen and (max-width: 700px) {
    #menu-toggle:checked ~ #cover {
        width: 100vw;
        height: 100vh;
        background-color: $primary-color;
    }

    #nav-bar {
        position: absolute;
        width: 100vw;
        height: 100vh;
        left: 0;
        top: 0;
    }

    .menu-button-container {
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: $transparent;
        height: 40px;
        width: 40px;
    }

    .nav-link {
        display: block;
        width: 100vw;
        background-color: $secondary-color;
        margin-top: 0;

        &::after {
            display: none;
        }

        &:active {
            filter: brightness(80%);
        }
    }

    #menu-toggle ~ #cover #menu {
        height: 0;
        transition: height 2s;
    }

    #menu-toggle:checked ~ #cover #menu {
        height: auto;
        transition: height 2s;
    }
}
</style>