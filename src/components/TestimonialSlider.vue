<script>
    export default{
        name: 'TestimonialSlider',

        data (){
            return {
                testimonials:[
                    {
                        name: 'Lily Du',
                        quote:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Voluptatum voluptate ea eius eos odio voluptas id reiciendis impedit consequatur',
                        occupation: 'student',
                        imgPath: '/img/testimonials-standard-1.png',
                    },{
                        name: 'Joan Collins',
                        quote:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Voluptatum voluptate ea eius eos odio voluptas id reiciendis impedit consequatur',
                        occupation: 'student',
                        imgPath: '/img/testimonials-standard-2.png',
                    },{
                        name: 'Jane Doe',
                        quote:'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Voluptatum voluptate ea eius eos odio voluptas id reiciendis impedit consequatur',
                        occupation: 'student',
                        imgPath: '/img/testimonials-standard-3.png',
                    }
                ],

                activeSlide: 0,
                
            }
        }
    }

</script>

<template>
    <div id="testimonial-bg">
        <!-- content of the testimonial populated from data -->
        
        <div
            v-for="(obj, index) in testimonials"
            class="testimonial"
            :class="{active: activeSlide == index}"
        >
            <div class="img-wrapper">
                <img :src="obj.imgPath" alt=""> 
            </div>
            
            <p>"{{ obj.quote }}"</p>
            <div>
                <h3>{{ obj.name }}</h3>
                <div><small>{{ obj.occupation.toUpperCase() }}</small></div>
            </div>
            
        </div>

        
        

        <!-- buttons to go throuh the slides -->
        <div class="slide-buttons">
            <button class="slide-btn"
                v-for="(obj, index) in testimonials"
                :class="{active: activeSlide == index}"
                @click="activeSlide = index">
            </button>
        </div>
    </div>
</template>

<style lang="scss">

    #testimonial-bg{
        // background img
        height: 645px;
        position: relative;
        background-image: url('/img/h5-parallax-img-1.png');
        background-position: top;
        overflow-x: hidden;

        
        .jumbo-img {
            height: 100%;
            object-fit: none;
            object-position: top;
        }

        // testimonial content
        .testimonial{
            position: absolute;
            top: 130px;
            left: 50%;
            transform: translateX(-50%);

            width: 65%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            gap: 1rem;
            
            line-height: 1.5rem;
            text-align: center;
            color: white;
            


            &.active{
                animation: fade-in 1s ease forwards;
            }

            &:not(.active){
                animation: fade-out 1s ease forwards;
            }

            .img-wrapper{
                width: 105px;
            }

            h3{
                font-size: 1.5rem;
                padding-bottom: 0.5rem;
            }

            small{
                font-weight: bold;
            }

            p{
                font-size: 1.2rem;

            }
        }

        // buttons
        .slide-buttons{
            position: absolute;
            left: 50%;
            bottom: 0;
            transform: translateX(-50%);

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
                    background-color: white;
                }
            }
        }
    }

    @keyframes fade-in {
        from{
            left: 100%
        }

        to{
            left: 50%;
            opacity: 1;
            visibility: visible;
        }
    }

    @keyframes fade-out {
        from{
            left: 50%;
            opacity: 1;
            visibility: visible;
        }
        to{
            left: 0;
            opacity: 0;
            visibility: hidden;
        }
    }

</style>