<template>
    <section>
        <app-header></app-header>
        <div class="container">
            <div class="row">
                <div class="col-12">
                    <transition name="slide" mode="out-in">
                        <router-view></router-view>
                    </transition>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    import Header from './components/Header.vue'

    export default {
        components: {
            appHeader: Header
        },
        created() {
            this.$store.dispatch('initStocks');
        }
    }
</script>

<style lang="scss">
    .container {
        padding-top: 50px;
    }
    @keyframes slide-in {
        from {
            transform: translateY(-30px);
            opacity: 0;
        }
        to {
            transform: translateY(0);
            opacity: 1;
        }
    }
    @keyframes slide-out {
        from {
            transform: translateY(0);
            opacity: 1;
        }
        to {
            transform: translateY(30px);
            opacity: 0;
        }
    }
    .slide-enter-active {
        animation: slide-in .2s ease-out forwards;
    }
    .slide-leave-active {
        animation: slide-out .2s ease-out forwards;
    }
</style>
