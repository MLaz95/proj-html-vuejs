<script>
    export default{
        name: 'NavBar',

        data (){
            return {
                navLinks: [
                    'home','courses','instructors','events','pages','elementes',
                ],

                dropDownIsOpen: false,
            }
        },

        methods: {
            toggleDropDown(){
                this.dropDownIsOpen = !this.dropDownIsOpen
            },

        },
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
            <button><i class="fa-solid fa-magnifying-glass"></i></button>
            <button id="cart-icon">
                <i class="fa-solid fa-bag-shopping"></i>
            </button>
            <button @click="toggleDropDown()"><i class="fa-solid fa-bars"></i></button>
            <ul class="dropdown-menu" :class="{active: dropDownIsOpen}" >
                <li class="dropdown-item" @click="$emit('stop')">Stop Autoplay</li>
                <li class="dropdown-item" @click="$emit('start')">Start Autoplay</li>
            </ul>
        </div>

    </nav>

</template>

<style lang="scss">
    @use '../styles/variables.scss' as *;

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
        z-index: 10;

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
            gap: 1.5rem;

            list-style: none;
            text-transform: uppercase;

            li{
                cursor: pointer;
                padding: 10px;
                transition: background-color 0.3s;

                &:hover{
                    background-color: rgba($color: #FFFFFF, $alpha: 0.3);
                }
            }
        }

        .button-group{
            display: flex;
            align-items: center;
            gap: 1rem;

            position: relative;

            button{
                font-size: 1rem;
                border: none;
                color: white;
                background-color: transparent;
                transition: transform 0.3s;

                &:hover{
                    transform: scale(1.2);
                }
            }
        }

        #cart-icon{
            position: relative;

            &::before{
                content: '0';
                font-size: 0.8rem;
                display: inline-block;
                width: 15px;
                height: 15px;

                position: absolute;
                top: -30%;
                right: -70%;
                
                border-radius: 50%;
                background-color: $bg-primary;
            }
        }

        .dropdown-menu{
            flex-direction: column;
            align-items: stretch;
            gap: 0;
            background-color: $bg-fourth;
            position: absolute;
            top: 100%;
            right: 0;

            &:not(.active){
                display: none;
            }

            .dropdown-item{
                cursor: pointer;
                text-align: right;
                text-wrap: nowrap;
                color: black;
                border-bottom: 1px solid $border-secondary;

                &:hover{
                    background-color: rgba($color: #000000, $alpha: 0.2)
                }
            }
        }
    }


</style>