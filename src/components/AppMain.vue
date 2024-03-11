<script>
    export default{
        name: 'AppMain',

        data(){
                return {
                    // list of links below header
                    cardLinks:['Languages', 'Software', 'Business', 'Chemistry', 'Science', 'DIY&Craft']
                }
            }

    }

    
</script>

<template>

    <section class="container">

        <div class="card-links">
            <div v-for="(link, index) in cardLinks" class="card">
                <img :src="`/img/h5-custom-icon-${index + 1}.png`" alt="">
                <div><strong>{{ link }}</strong></div>
            </div>
        </div>
        
        <div class="section-text">
            <h2>The Trusted Name<br> for In-Home Tutoring.</h2>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Accusantium sed suscipit quo, rerum voluptatem deleniti harum nostrum ducimus voluptatum hic sit ipsa, quisquam veniam repellendus, non culpa odio ratione minus?</p>
            <a href="!#">Learn More</a>
        </div>

        <div class="img-wrapper">
            <img src="/img/h5-img-1.jpg" alt="">
            <button class="btn-top">
                <i class="fa-solid fa-chevron-up"></i>
                <div>TOP</div>
            </button>
        </div>
    </section>

    <section class="split-section container">
        <div>
            <!-- img -->
            <img src="/img/h5-img-2.jpg" alt="">
        </div>
        <div class="split-text">
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

    

</template>

<style lang="scss">
@use '../styles/variables.scss' as *;

    section{
        .img-wrapper{
            max-width: 1100px;

            img{
                width: 100%;
            }
        }

        
    }
    .card-links{
        display: flex;
        justify-content: space-around;

        margin: 60px 0 120px;

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

    .container.split-section{
        display: flex;
        margin: 100px auto 50px;
        div{
            width: 50%;
            img{
                width: 100%;
            }
        }

        .split-text{
            padding: 0 115px 0 60px ;
            p{
                margin: 1rem 0;
            }   
        }

        .section-data{
            width: 100%;
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
    }
</style>