<script>
    export default{
        name: 'NavBar',

        data (){
            return {
                navLinks: [
                    'home','courses','instructors','events','pages','elementes',
                ]
            }
        }
    }

</script>

<template>
    <nav>
        <div class="img-wrapper">
            <!-- logo -->
            <img src="/img/logo-light.png" alt="">
        </div>

        
            <!-- links -->
        <ul>
            <li v-for="link in navLinks">{{ link }}</li>
        </ul>
        

        <div class="button-group">
            <!-- buttons -->
            <div><i class="fa-solid fa-magnifying-glass"></i></div>
            <div><i class="fa-solid fa-bag-shopping"></i></div>
            <div><i class="fa-solid fa-bars"></i></div>
        </div>

    </nav>

</template>

<style lang="scss">
    nav{
        background-color: transparent;
        width: 100%;
        padding: 2rem;
        display: flex;
        justify-content: space-between;
        align-items: stretch;
        position: absolute;
        top: 0;
        left: 0;

        font-size: 1rem;
        color: white;

        .img-wrapper{
            height: 2rem;

            img{
                height: 100%;
            }
        }

        ul{
            align-items: center;
            display: flex;
            gap: 2rem;

            list-style: none;
            text-transform: uppercase;
        }

        .button-group{
            display: flex;
            align-items: center;
            gap: 1rem;
        }
    }


</style>