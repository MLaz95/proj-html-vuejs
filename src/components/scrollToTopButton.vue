<script>
    export default{
        name: 'scrollToTopButton',

        data(){
            return{
                isVisible: false,

            }
        },

        methods:{
            // shows the button when you scroll down, hides it at the top of the page
            showButton(){
                if(document.documentElement.scrollTop > 50){
                    this.isVisible = true;
                }
                 else{
                    this.isVisible = false;
                }
            },

            // scrolls back to top
            topFunction(){
                window.scrollTo({top: 0, behavior: 'smooth'})
            }
        },

        created(){
            window.addEventListener('scroll', this.showButton);
        },

        beforeUnmount(){
            window.removeEventListener('scroll', this.showButton);
        }




    }
</script>

<template>
    <button class="btn-top" @click="topFunction()" v-if="isVisible">
            <i class="fa-solid fa-chevron-up"></i>
            <div>TOP</div>
        </button>
</template>

<style lang="scss">
    @use '../styles/variables.scss' as *;

    .btn-top{
    cursor: pointer;
    position: fixed;
    bottom: 150px;
    right: 0;
    z-index: 10;

    padding: 1rem;
    border: none;
    font-weight: bold;
    color: white;
    background-color: $bg-primary;
    }
</style>