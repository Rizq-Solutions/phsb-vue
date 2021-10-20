<template>
    <div class="layout-topbar">
        <a class="menu-button" @click="$emit('menubutton-click')">
            <i class="pi pi-bars"></i>
        </a>
        <router-link to="/" class="logo">
            <img alt="logo" src="./assets/images/primevue-logo.png">
        </router-link>
        <div class="app-theme" v-tooltip.bottom="theme">
            <img :src="'demo/images/themes/' + logoMap[theme]" />
        </div>
        <ul ref="topbarMenu" class="topbar-menu">
            <li><router-link to="./">Back to Home</router-link></li>
            <li class="topbar-submenu">
                <a tabindex="0" @click="toggleMenu($event, 0)">
                    <span v-badge.danger>About Us</span>
                </a>
                <transition name="p-connected-overlay" @enter="onMenuEnter">
                    <ul v-show="activeMenuIndex === 0">
                        <li class="topbar-submenu-header">PROFILES</li>
                        <li><router-link to="/theming"><i class="pi pi-fw pi-file"/><span>Guide</span></router-link></li>
                        <li><a href="https://www.primefaces.org/designer/primevue"><i class="pi pi-fw pi-palette" /><span>Designer</span></a></li>
                        <li><a href="https://www.primefaces.org/designer-vue"><i class="pi pi-fw pi-desktop" /><span>Visual Editor</span></a></li>
                        <li><router-link to="/icons"><i class="pi pi-fw pi-info-circle"/><span>Icons</span></router-link></li>


                    </ul>
                </transition>
            </li>
            <li class="topbar-submenu">
                <a tabindex="0" @click="toggleMenu($event, 1)">Support</a>
                <transition name="p-connected-overlay" @enter="onMenuEnter">
                    <ul v-show="activeMenuIndex === 1"><li class="topbar-submenu-header">PREMIUM ADMIN TEMPLATES</li>
                        <li><a href="https://www.primefaces.org/layouts/atlantis-vue"><img src="./assets/images/layouts/themeswitcher-atlantis.svg" alt="Atlantis" /><span>Atlantis</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/freya-vue"><img src="./assets/images/layouts/themeswitcher-freya.png" alt="Freya" /><span>Freya</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/diamond-vue"><img src="./assets/images/layouts/themeswitcher-diamond.png" alt="Diamond" /><span>Diamond</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/sapphire-vue"><img src="./assets/images/layouts/themeswitcher-sapphire.png" alt="Sapphire" /><span>Sapphire</span><span class="theme-badge material">material</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/serenity-vue"><img src="./assets/images/layouts/themeswitcher-serenity.png" alt="Serenity" /><span>Serenity</span><span class="theme-badge material">material</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/ultima-vue"><img src="./assets/images/layouts/themeswitcher-ultima.png" alt="Ultima" /><span>Ultima</span><span class="theme-badge material">material</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/avalon-vue"><img src="./assets/images/layouts/themeswitcher-avalon.png" alt="Avalon" /><span>Avalon</span><span class="theme-badge bootstrap">bootstrap</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/babylon-vue"><img src="./assets/images/layouts/themeswitcher-babylon.png" alt="Babylon" /><span>Babylon</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/apollo-vue"><img src="./assets/images/layouts/themeswitcher-apollo.png" alt="Apollo" /><span>Apollo</span><span class="theme-badge darkmode">dark mode</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/roma-vue"><img src="./assets/images/layouts/themeswitcher-roma.jpg" alt="Roma" /><span>Roma</span></a></li>
                        <li><a href="https://www.primefaces.org/layouts/prestige-vue"><img src="./assets/images/layouts/themeswitcher-prestige.png" alt="Prestige" /><span>Prestige</span></a></li>
                    </ul>
                </transition>
            </li>
            <li class="topbar-submenu topbar-resources-submenu">
                <a tabindex="0" @click="toggleMenu($event, 2)">My account</a>
                <transition name="p-connected-overlay" @enter="onMenuEnter">
                    <ul v-show="activeMenuIndex === 2">
                        <li><router-link to="/support"><span>Support</span></router-link></li>
                        <li><a href="https://forum.primefaces.org/viewforum.php?f=110"><span>Help</span></a></li>
                        <li><a href="https://discord.gg/gzKFYnpmCY" target="_blank"><span>Chat Messenger</span></a></li>
                        <li><a href="https://www.primetek.com.tr" target="_blank"><span>Notifications</span></a></li>
                    </ul>
                </transition>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    outsideClickListener: null,
    darkDemoStyle: null,
    watch: {
        $route() {
            this.activeMenuIndex = null;
        }
    },
    props: {
        theme: null
    },
    data() {
        return {
            activeMenuIndex: null,
            logoMap: {
                'bootstrap4-light-blue': 'bootstrap4-light-blue.svg',
                'bootstrap4-light-purple': 'bootstrap4-light-purple.svg',
                'bootstrap4-dark-blue': 'bootstrap4-dark-blue.svg',
                'bootstrap4-dark-purple': 'bootstrap4-dark-purple.svg',
                'md-light-indigo': 'md-light-indigo.svg',
                'md-light-deeppurple': 'md-light-deeppurple.svg',
                'md-dark-indigo': 'md-dark-indigo.svg',
                'md-dark-deeppurple': 'md-dark-deeppurple.svg',
                'mdc-light-indigo': 'md-light-indigo.svg',
                'mdc-light-deeppurple': 'md-light-deeppurple.svg',
                'mdc-dark-indigo': 'md-dark-indigo.svg',
                'mdc-dark-deeppurple': 'md-dark-deeppurple.svg',
                'saga-blue': 'saga-blue.png',
                'saga-green': 'saga-green.png',
                'saga-orange': 'saga-orange.png',
                'saga-purple': 'saga-purple.png',
                'vela-blue': 'vela-blue.png',
                'vela-green': 'vela-green.png',
                'vela-orange': 'vela-orange.png',
                'vela-purple': 'vela-purple.png',
                'arya-blue': 'arya-blue.png',
                'arya-green': 'arya-green.png',
                'arya-orange': 'arya-orange.png',
                'arya-purple': 'arya-purple.png',
                'nova': 'nova.png',
                'nova-alt': 'nova-alt.png',
                'nova-accent': 'nova-accent.png',
                'nova-vue': 'nova-vue.png',
                'luna-blue': 'luna-blue.png',
                'luna-green': 'luna-green.png',
                'luna-pink': 'luna-pink.png',
                'luna-amber': 'luna-amber.png',
                'rhea': 'rhea.png',
                'fluent-light': 'fluent-light.png',
                'soho-light': 'soho-light.png',
                'soho-dark': 'soho-dark.png',
                'viva-light': 'viva-light.svg',
                'viva-dark': 'viva-dark.svg',
                'mira': 'mira.jpg',
                'nano': 'nano.jpg',
                'tailwind-light': 'tailwind-light.png',
            }
        }
    },
    methods: {
        changeTheme(event, theme, dark) {
            this.$emit('change-theme', {theme: theme, dark: dark});
            this.activeMenuIndex = null;
            event.preventDefault();
        },
        toggleMenu(event, index) {
            this.activeMenuIndex = (this.activeMenuIndex === index) ? null : index;
            event.preventDefault();
        },
        onMenuEnter() {
            this.bindOutsideClickListener();
        },
        bindOutsideClickListener() {
            if (!this.outsideClickListener) {
                this.outsideClickListener = (event) => {
                    if ((this.activeMenuIndex != null && this.isOutsideTopbarMenuClicked(event))) {
                        this.activeMenuIndex = null;
                        this.unbindOutsideClickListener();
                    }
                };
                document.addEventListener('click', this.outsideClickListener);
            }
        },
        unbindOutsideClickListener() {
            if (this.outsideClickListener) {
                document.removeEventListener('click', this.outsideClickListener);
                this.outsideClickListener = null;
            }
        },
        isOutsideTopbarMenuClicked(event) {
            return !(this.$refs.topbarMenu.isSameNode(event.target) || this.$refs.topbarMenu.contains(event.target));
        }
    }
}
</script>
