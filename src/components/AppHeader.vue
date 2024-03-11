<script>
    import NavBar from './NavBar.vue';
    
    export default{
        name: 'AppHeader',
        components:{
            NavBar,
        },
    }

</script>

<template>
    <header>
        <NavBar></NavBar>
        <img src="/img/h5-slide-3-background.jpg" alt="">
        <div class="head-text">
            <h1>Contemporary Ideas</h1>
            <p>
                Lorem ipsum, dolor sit amet consectetur adipisicing elit. Suscipit nobis molestiae architecto soluta provident esse sit vel assumenda in natus!
            </p>
            <button>Register Now</button>
        </div>
    </header>


</template>

<style lang="scss">
    header{
        position: relative;
        img{
            width: 100%;
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
    }

</style>