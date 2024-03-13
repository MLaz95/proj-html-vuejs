<script>
    import NavBar from './NavBar.vue';
    
    export default{
        name: 'AppHeader',
        components:{
            NavBar,
        },

        data(){
            return{
            
                headSlides: [
                    {
                        background: '/img/h5-slide-1-background.jpg',
                        title: 'Contemporary Ideas',
                        text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse dapibus, sem a ornare tristique, dolor nibh fringilla sem, rhoncus semper libero quam vitae nisi.'
                    },{
                        background: '/img/h5-slide-2-background.jpg',
                        title: 'Title 2',
                        text: 'Donec rutrum velit interdum nulla malesuada vehicula. Suspendisse potenti. Aliquam in velit tristique, placerat nibh non, porta mauris.'
                    },{
                        background: '/img/h5-slide-3-background.jpg',
                        title: 'Title 3',
                        text: 'Maecenas at risus leo. Duis malesuada feugiat nulla sed luctus. Phasellus id fermentum neque. Nam feugiat porttitor maximus. Nullam ac erat ultrices metus suscipit sollicitudin nec in sem.'
                    }
                ],

                activeSlide: 0,
            }
        },

        methods:{
            nextSlide(){
                if(this.activeSlide < 2){
                    this.activeSlide++;
                }else{
                    this.activeSlide = 0;
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
        <div class="head-view">

            <div v-for="(slide,index) in headSlides" class="slide" :class="{active: activeSlide == index}">
                <img :src="slide.background" alt="">
        
                <div class="head-text">
                    <h1>{{ slide.title }}</h1>
                    <p>
                        {{ slide.text }}
                    </p>
                    <button class="btn">Register Now</button>
                </div>
            </div>

            
            <div class="head-buttons">
                <div class="slide-controls">
                    <button
                        v-for="(slide, index) in headSlides"
                        :class="{active: activeSlide == index}"
                        @click="activeSlide = index">
                    </button>

                </div>
            </div>
        </div>
    </header>


</template>

<style lang="scss">
    @use '../styles/variables.scss' as *;

    header{
        .head-view{
            position: relative;
            width: 100%;
            height: 680px;

            .slide{
                position: absolute;
                width: 100%;
                height: 100%;
    
                &:not(.active){
                    animation: head-fade-out 0.3s ease forwards;
                }
                
                &.active{
                    animation: head-fade-in 0.3s ease forwards;
                }
                img{
                    width: 100%;
                    height: 100%;
                    object-fit: cover;
                    object-position: top;
                }
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
                border: none;
                text-transform: uppercase;
                color: white;
                background-color: $bg-primary;
            }
        
            .head-buttons{
                position: absolute;
                left: 50%;
                bottom: 0;
                transform: translateX(-50%);
                display: flex;
                flex-direction: column;
                align-items: center;
        
                .slide-controls{
                    display: flex;
                    gap: 1rem;
                    padding: 2rem;
                    
                    button{
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
            }

        }




    }
    
    @keyframes head-fade-out {
        from{
            opacity: 1;
            visibility: visible;
        }

        to{
            opacity: 0;
            visibility: hidden;
        }
    }
    @keyframes head-fade-in {
        from{
            opacity: 0;
            visibility: hidden;
        }

        to{
            opacity: 1;
            visibility: visible;
        }
    }
</style>