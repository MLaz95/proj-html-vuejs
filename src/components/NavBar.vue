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
            <div>search</div>
            <div>cart</div>
            <div>menu</div>
        </div>

    </nav>

</template>

<style lang="scss">
    nav{
        background-color: pink;
        height: 100px;
        // test
        width: 100%;
        padding: 2rem;
        display: flex;
        justify-content: space-between;
        align-items: stretch;

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