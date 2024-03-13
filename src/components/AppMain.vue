<script>
    import TestimonialSlider from './TestimonialSlider.vue';
    import BenefitTabs from './BenefitTabs.vue';
    import CourseCarousel from './CourseCarousel.vue';
    import PricingChart from './PricingChart.vue';
    import scrollToTopButton from './scrollToTopButton.vue';

    export default{
        name: 'AppMain',
        components:{
            TestimonialSlider,
            BenefitTabs,
            CourseCarousel,
            PricingChart,
            scrollToTopButton,
        },

        data(){
            return {
                // list of links below header
                cardLinks:['Languages', 'Software', 'Business', 'Chemistry', 'Science', 'DIY&Craft'],
                clientLogos: [
                    {name: 'iAcademy', imgPath:'/img/h5-client-1.png'},
                    {name: 'Study Central University', imgPath:'/img/h5-client-2.png'},
                    {name: 'Educator', imgPath:'/img/h5-client-3.png'},
                    {name: 'Scholar University', imgPath:'/img/h5-client-4.png'}
                ]
            }
        },


    }

    
</script>

<template>


    <div class="container">
        <!-- side button that scrolls page back to top -->
        <scrollToTopButton></scrollToTopButton>

        <!-- card links populated with array -->
        <div class="card-links">
            <div v-for="(link, index) in cardLinks" class="card">
                <img :src="`/img/h5-custom-icon-${index + 1}.png`" alt="">
                <div><strong>{{ link }}</strong></div>
            </div>
        </div>
        
        <section id="intro">
            <!-- first section -->
            <div class="head">
                <h2>The Trusted Name<br> for In-Home Tutoring.</h2>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium sed suscipit quo, rerum voluptatem deleniti harum nostrum ducimus voluptatum hic sit ipsa, quisquam veniam repellendus, non culpa odio ratione minus?</p>
                <a href="#!">Learn More</a>
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

    <BenefitTabs></BenefitTabs>

    <section id="courses">
        <div class="container">
            <div class="head">
                <h2>Popular Online Courses</h2>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ratione alias, quaerat facilis consequuntur animi repellat ducimus omnis atque iusto! Quod eius voluptates adipisci voluptatem nesciunt facilis, quam cupiditate est quia.</p>
            </div>
            <CourseCarousel></CourseCarousel>
        </div>
    </section>

    <section id="pricing">
        <div class="head">
            <h2>Pricing Plans</h2>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
        </div>
        <PricingChart></PricingChart>
    </section>

    <section class="client-logos">
        <div class="container">
            <img :src="client.imgPath" :alt="client.name" v-for="client in clientLogos">
        </div>
    </section>

</template>

<style lang="scss" scoped>
@use '../styles/variables.scss' as *;

    section{
        padding: 50px 0 50px;

        &#intro p{
            padding-bottom: 1rem;
        }

        .img-wrapper{
            max-width: 1100px;

            img{
                width: 100%;
            }
        }

        .head{
            padding-bottom: 100px;

            h2{
                padding-bottom: 1rem;
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
    }

    .card-links{
        display: flex;
        justify-content: space-between;

        padding: 60px 0;

        .card{
            cursor: pointer;
            width: 140px;
            padding: 27px 0;
            border: 2px solid $border-primary;

            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 2rem;

            background-color: $bg-secondary;
            transition: background-color 0.3s, border-color 0.3s;

            &:hover{
                background-color: white;
                border-color: $bg-primary;
            }
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
        text-wrap: nowrap;
        color: $bg-primary;
        
        div{
            width: 50%;
            font-weight: bold;

            strong{
                font-size: 3rem;
            }
        }
    }

    #courses{
        padding: 120px 0;
        border-top: 2px solid $border-secondary;
        border-bottom: 2px solid $border-secondary;
        text-align: center;
        background-image: url(/img/page-background-img.png);
    }

    #pricing{
        text-align: center;
        background-image: url(/img/page-background-img.png);
    }

    .client-logos{
        display: flex;
        justify-content: center;
        border-top: 1px solid $border-primary;

        img{
            width: calc(100% / 4);
            padding: 40px 0;
        }
    }
</style>