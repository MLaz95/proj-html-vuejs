<script>
    import NavBar from './NavBar.vue';
    
    export default{
        name: 'AppHeader',
        components:{
            NavBar,
        },

        data(){
            return{
                activeSlide: 1,
            }
        },

        methods:{
            nextSlide(){
                if(this.activeSlide < 3){
                    this.activeSlide++;
                }else{
                    this.activeSlide = 1;
                }
            }
        },

        mounted(){
            // setInterval(this.nextSlide, 3000)
        }


    }

</script>

<template>
    <header>
        <NavBar></NavBar>
        <img src="/img/h5-slide-1-background.jpg" alt="" v-show="activeSlide == 1">
        <img src="/img/h5-slide-2-background.jpg" alt="" v-show="activeSlide == 2">
        <img src="/img/h5-slide-3-background.jpg" alt="" v-show="activeSlide == 3">
        <div class="head-text">
            <h1>Contemporary Ideas</h1>
            <p>
                Lorem ipsum, dolor sit amet consectetur adipisicing elit. Suscipit nobis molestiae architecto soluta provident esse sit vel assumenda in natus!
            </p>
            <button class="btn">Register Now</button>
        </div>
        <div class="slide-buttons">
            <button class="slide-btn" :class="{active: activeSlide == 1}" @click="activeSlide = 1"></button>
            <button class="slide-btn" :class="{active: activeSlide == 2}" @click="activeSlide = 2"></button>
            <button class="slide-btn" :class="{active: activeSlide == 3}" @click="activeSlide = 3"></button>
        </div>
    </header>


</template>

<style lang="scss">
    @use '../styles/variables.scss' as *;

    header{
        position: relative;
        img{
            width: 100%;
            height: 100%;
        }
        
        .head-text{
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);

            text-align: center;
            color: white;

            h1{
                font-size: 4rem;
                text-wrap: nowrap;
            }

            p{
                font-size: 1rem;
                line-height: 1.5rem;
                margin: 1rem 0;
            }
        }

        .btn{
            padding: 1rem 2rem;
            background-color: $bg-primary;
            border: none;
            color: white;
            text-transform: uppercase;
        }

        .slide-buttons{
            position: absolute;
            left: 50%;
            bottom: 0;
            transform: translateX(-50%);

            display: flex;
            gap: 1rem;
            padding: 2rem;
        }

        .slide-btn{
            width: 16px;
            height: 16px;

            border: none;
            border-radius: 50%;

            background-color: rgba($color: #F2F2F2, $alpha: 0.5);

            &.active{
                border: 2px solid white;
                position: relative;

                &::after{
                    content: '';
                    width: 8px;
                    height: 8px;
                    border-radius: 50%;
                    position: absolute;
                    top: 50%;
                    left: 50%;
                    transform: translate(-50%, -50%);
                    background-color: white;
                }
            }
        }
    }

</style>