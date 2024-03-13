<script>
    export default{
        name: 'loader',

        data(){
            return{
                isLoaded: false,
            }
        },

        methods:{
            endLoad(){
                this.isLoaded = true;
            }
        },

        mounted(){
            setTimeout(this.endLoad, 600)
        }
    }
</script>

<template>
    <div id="loader" :class="{vanish: isLoaded}">
        <div>
            <img src="/img/logo-light.png" alt="">
            <div id="loading-bar">
                <div></div>
            </div>
        </div>
    </div>
    
</template>

<style lang="scss">
    @use '../styles/variables.scss' as *;

    #loader{
        width: 100vw;
        height: 100vh;
        position: fixed;
        z-index: 99;
        overflow: hidden;
        background-color: $bg-primary;

        & > div{
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        #loading-bar{
            // width: 100%;
            height: 5px;
            border-radius: 3px;
            background-color: $bg-tertiary;
            position: relative;

            & > div{
                height: 5px;
                position: absolute;
                top: 0;
                left: 0;
                border-radius: 3px;
                background-color: white;

                animation: load 0.5s linear forwards;
            }
        }

        &.vanish{
            animation: vanish 0.4s ease forwards;
        }
    }

    @keyframes load {
        from{
            width: 0;
        }

        to{
            width: 100%;
        }
    }

    @keyframes vanish{
        from{
            opacity: 1;
            visibility: visible;
        }

        to{
            opacity: 0;
            visibility: hidden;
        }
    }

</style>