<template>
    <div id="nav-bar">
        <input id="menu-toggle" type="checkbox" />
        <label id="menu-button-container" for="menu-toggle">
            <div id="menu-button"></div>
        </label>
        <div id="toggle-background"></div>
        <nav id="menu">
            <router-link class="nav-link" to="/">Home</router-link>
            <router-link class="nav-link" to="/gallery">Gallery</router-link>
            <router-link class="nav-link" to="/about">About</router-link>
        </nav>
    </div>
</template>

<style lang="scss">
@import '@/scss/dark-colors.scss';

.nav-link {
    padding: 1em;
    margin-top: 2px;
    display: inline-block;
    text-decoration: none;
    color: $link-color;
    background-color: $primary-color;

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

#menu-toggle {
    display: none;
}

#menu-button-container {
    display: none;
}

@media only screen and (max-width: 700px) {
    #nav-bar {
        position: absolute;
        width: 100vw;
        height: 100vh;
        left: 0;
        top: 0;
    }

    #menu {
        overflow: hidden;
        display: flex;
        flex-direction: column;
        row-gap: 1em;
    }

    #menu-button-container {
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: $transparent;
        height: 40px;
        width: 40px;
        z-index: 2;
    }

    .nav-link {
        display: block;
        width: 100vw;
        background-color: $secondary-color;
        margin-top: 0;
        padding: 0;
        padding-top: 1.5em;
        padding-bottom: 1.5em;
        box-sizing: border-box;
        z-index: 2;

        &::after {
            display: none;
        }

        &:active {
            filter: brightness(80%);
        }
    }

    #menu-button,
    #menu-button::before,
    #menu-button::after {
        display: block;
        background-color: #fff;
        height: 4px;
        width: 30px;
        transition: transform 400ms cubic-bezier(0.23, 1, 0.32, 1);
        border-radius: 2px;
        z-index: 2;
    }

    #menu-button::before {
        content: '';
        margin-top: -8px;
    }

    #menu-button::after {
        content: '';
        margin-top: 12px;
    }

    #menu-toggle:checked + .menu-button-container .menu-button {
        background: rgba(255, 255, 255, 0);
        z-index: 1;
    }

    #menu-toggle:checked + .menu-button-container .menu-button::before {
        margin-top: 0px;
        transform: rotate(405deg);
    }

    #menu-toggle:checked + .menu-button-container .menu-button::after {
        margin-top: -4px;
        transform: rotate(-405deg);
    }

    #menu-toggle ~ #menu {
        height: 0;
        transition: height 2s;
    }

    #menu-toggle:checked ~ #menu {
        height: auto;
        transition: height 2s;
    }

    #menu-toggle:checked ~ #toggle-background {
        top: 0;
        left: 0;
        position: absolute;
        width: 100vw;
        height: 100vh;
        background-color: $primary-color;
    }
}
</style>