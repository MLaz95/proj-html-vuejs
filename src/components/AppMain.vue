<script>
    import TestimonialSlider from './TestimonialSlider.vue'
    export default{
        name: 'AppMain',
        components:{
            TestimonialSlider,
        },

        data(){
            return {
                // list of links below header
                cardLinks:['Languages', 'Software', 'Business', 'Chemistry', 'Science', 'DIY&Craft']
            }
        },


    }

    
</script>

<template>

    <div class="container">
        <!-- side button that scrolls page back to top -->
        <button class="btn-top">
            <i class="fa-solid fa-chevron-up"></i>
            <div>TOP</div>
        </button>

        <!-- card links populated with array -->
        <div class="card-links">
            <div v-for="(link, index) in cardLinks" class="card">
                <img :src="`/img/h5-custom-icon-${index + 1}.png`" alt="">
                <div><strong>{{ link }}</strong></div>
            </div>
        </div>
        
        <section>
            <!-- first section -->
            <div class="section-text">
                <h2>The Trusted Name<br> for In-Home Tutoring.</h2>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium sed suscipit quo, rerum voluptatem deleniti harum nostrum ducimus voluptatum hic sit ipsa, quisquam veniam repellendus, non culpa odio ratione minus?</p>
                <a href="!#">Learn More</a>
            </div>
    
            <!-- bg img between sections -->
            <div class="img-wrapper">
                <img src="/img/h5-img-1.jpg" alt="">
            </div>
        </section>
    
        <!-- second section w/ 2 column layout -->
        <section class="row">
            <div class="col-6">
                <!-- img -->
                <img class="img-fluid" src="/img/h5-img-2.jpg" alt="">
            </div>
            <div class="col-6 text">
                <!-- text -->
                <h2>Empowering Children to Reach Their Potential.</h2>
                <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Quam aperiam error quas sit hic sed? Odit, tempora itaque odio saepe, aliquid exercitationem esse numquam, recusandae officia enim possimus. Sint, doloribus.</p>
                <div class="section-data">
                    <div>
                        <div><strong>168</strong></div>
                        <div>User Stories</div>
                    </div>
                    <div>
                        <div><strong>347</strong></div>
                        <div>Events</div>
                    </div>
                </div>
            </div>
        </section>
    </div>
    <TestimonialSlider></TestimonialSlider>


    

</template>

<style lang="scss" scoped>
@use '../styles/variables.scss' as *;

    .btn-top{
    position: fixed;
    bottom: 150px;
    right: 0;
    padding: 1rem;
    border: none;
    font-weight: bold;
    color: white;
    background-color: $bg-primary;
    }

    section{
        padding: 50px 0 50px;

        .img-wrapper{
            max-width: 1100px;

            img{
                width: 100%;
            }
        }

        
    }
    .card-links{
        display: flex;
        justify-content: space-between;

        padding: 60px 0;

        .card{
            width: 140px;
            padding: 27px 0;
            border: 2px solid $border-primary;

            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 2rem;

            background-color: $bg-secondary;
        }
    }

    .section-text{
        display: flex;
        flex-direction: column;

        p{
            margin: 1rem 0;
        }

        a{
            border: none;
            font-weight: bold;
            text-transform: uppercase;
            text-decoration: none;
            color: $bg-primary;
            background-color: transparent;
        }
    }

    .text{
        padding: 0 115px 0 60px ;
        p{
            margin: 1rem 0;
        }   
    }

    .section-data{
        display: flex;
        color: $bg-primary;
        
        div{
            width: 50%;
            font-weight: bold;

            strong{
                font-size: 3rem;
            }
        }
    }
</style>