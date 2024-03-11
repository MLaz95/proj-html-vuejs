<script>
    export default{
        name: 'AppMain',

        data(){
                return {
                    cardLinks:[
                        'Languages', 'Software', 'Business', 'Chemistry', 'Science', 'DIY&Craft'
                    ]
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
    </section>
    

</template>

<style lang="scss">
@use '../styles/variables.scss' as *;

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
</style>