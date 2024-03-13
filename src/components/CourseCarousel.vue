<script>
    export default{
        name: 'CourseCarousel',

        data(){
            return{
                // three arrays one for each slide, each array has three objects with all the info for each course
                courses:[[
                    {
                        name: 'Creative Writing',
                        teacher: 'Kevin Barton',
                        text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Fugit dolor nobis eligendi quas iure aut ipsam facere eius eveniet neque pariatur.Lorem ipsum dolor sit, amet consectetur adipisicing elit. Fugit dolor nobis eligendi quas iure aut ipsam facere eius eveniet neque pariatur.',
                        cost: 'free',
                        field: 'art',
                        slots: '1',
                        imgPath: '/img/course-1-f-img.jpg',
                    },{
                        name: '20th-century Literature',
                        teacher: 'Vivian McCray',
                        text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Fugit dolor nobis eligendi quas iure aut ipsam facere eius eveniet neque pariatur.',
                        cost: '15$',
                        field: 'art',
                        slots: '3',
                        imgPath: '/img/course-2-f-img.jpg',
                    },{
                        name: 'Architetctural Design 101',
                        teacher: 'Alison Clark',
                        text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Fugit dolor nobis eligendi quas iure aut ipsam facere eius eveniet neque pariatur.',
                        cost: '$35',
                        field: 'art',
                        slots: '4',
                        imgPath: '/img/course-3-f-img.jpg',
                    }
                ],[
                    {
                        name: 'Android Developer',
                        teacher: 'David Sanders',
                        text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Fugit dolor nobis eligendi quas iure aut ipsam facere eius eveniet neque pariatur.',
                        cost: 'free',
                        field: 'programming',
                        slots: '1',
                        imgPath: '/img/course-4-f-img.jpg',
                    },{
                        name: 'Web Designing',
                        teacher: 'Jennifer Powell',
                        text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Fugit dolor nobis eligendi quas iure aut ipsam facere eius eveniet neque pariatur.',
                        cost: 'free',
                        field: 'programming',
                        slots: '1',
                        imgPath: '/img/course-5-f-img.jpg',
                    },{
                        name: 'Financial Modeling',
                        teacher: 'Edward Bowman',
                        text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Fugit dolor nobis eligendi quas iure aut ipsam facere eius eveniet neque pariatur.',
                        cost: '$20',
                        field: 'business',
                        slots: '1',
                        imgPath: '/img/course-6-f-img.jpg',
                    }
                ],[
                    {
                        name: 'Social Media Management',
                        teacher: 'David Sanders',
                        text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Fugit dolor nobis eligendi quas iure aut ipsam facere eius eveniet neque pariatur.',
                        cost: '15$',
                        field: 'business',
                        slots: '2',
                        imgPath: '/img/course-7-f-img.jpg',
                    },{
                        name: 'Photography',
                        teacher: 'Faith Sellers',
                        text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Fugit dolor nobis eligendi quas iure aut ipsam facere eius eveniet neque pariatur.',
                        cost: 'free',
                        field: 'art',
                        slots: '1',
                        imgPath: '/img/course-8-f-img.jpg',
                    },{
                        name: 'Macroeconomics',
                        teacher: 'Thomas Navarro',
                        text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Fugit dolor nobis eligendi quas iure aut ipsam facere eius eveniet neque pariatur.',
                        cost: '$30',
                        field: 'business',
                        slots: '5',
                        imgPath: '/img/course-9-f-img.jpg',
                    }
                ]
                ],
                
                // responsible for which slide is active
                activeSlide: 0,
            }
        },
    }
</script>
<template>
    <div id="course-carousel">
        <!-- this carousel three slides, each slides contains three course-cards -->
        <div class="slide-view">
            <div class="slide" v-for="(slide, index) in courses" :class="{active: activeSlide == index}">
                <div class="card" v-for="course in slide">
                    <img :src="course.imgPath" alt="" class="img-fluid">
                    <div class="card-info">
                        <div class="card-head">
                            <div>
                                <div><strong>{{ course.name }}</strong></div>
                                <div><small>{{ course.teacher }}</small></div>
                            </div>
                            <div class="cost" :class="{free: course.cost == 'free'}"><small>{{ course.cost }}</small></div>
                        </div>
                        
                        <p>{{ course.text }}</p>
                        <div class="card-tags">
                            <div><i class="fa-solid fa-user"></i> {{ course.slots }} </div>
                            <div><i class="fa-solid fa-tag"></i> {{ course.field }}</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="slide-buttons">
            <button class="slide-btn"
                v-for="(slideArray, index) in courses"
                :class="{active: activeSlide == index}"
                @click="activeSlide = index">
            </button>
        </div>
    </div>
</template>

<style lang="scss">
    @use '../styles/variables.scss' as *;

    #course-carousel{
        padding-bottom: 100px;
        position: relative;
        
        .slide-view{
            height: 450px;
            position: relative;
            display: flex;
            gap: 30px;
            overflow-x: hidden;

        }
        .slide{
            position: absolute;
            width: 100%;
            top: 0;
            left: 0;
            display: flex;
            min-width: 100%;
            // flex-wrap: nowrap;
            gap: 30px;

            &.active{
                animation: course-fade-in 1s ease forwards;
            }

            &:not(.active){
                animation: course-fade-out 1s ease forwards;
            }

            .card{
                border: 2px solid $border-primary;
                width: calc(100% / 3 - 30px * 2 / 3);
                max-height: 450px;
                background-color: white;

                .card-info{
                    padding: 1rem;
                    display: flex;
                    flex-direction: column;
                    gap: 1rem;
                    text-align: start;
                    color: $text-secondary;

                    p{
                        flex-basis: 130px;
                        overflow-y: auto;
                    }

                    .card-head{
                        display: flex;
                        justify-content: space-between;
                        // align-items: start;
                        
                        strong{
                            color: black;
                            text-wrap: nowrap;
                        }

                        .cost{
                            text-transform: uppercase;
                            width: 50px;
                            height: 20px;
                            border-radius: 10px;
                            text-align: center;
                            color: white;
                            background-color: $bg-primary;
                            display: flex;
                            justify-content: center;
                            align-items: center;

                            &.free{
                                background-color: $bg-free;
                            }
                        }

                    }
                
                    .card-tags{
                        display: flex;
                        gap: 1rem;
                        font-size: 0.8rem;
                        text-transform: uppercase;
                    }
                }
            }

        }
        .slide-buttons{
            position: absolute;
            left: 50%;
            bottom: 0;
            transform: translateX(-50%);
    
            display: flex;
            gap: 1rem;
            padding: 2rem;
    
            button{
                width: 12px;
                height: 12px;
    
                border: none;
                border-radius: 50%;
    
                background-color: $bg-tertiary;
    
                &.active{
                    background-color: $bg-primary;
                }
            }
        }

    }

    @keyframes course-fade-in {
        from{
            left: 100%;
            opacity: 0;
            visibility: hidden;
        }

        to{
            left: 0;
            opacity: 1;
            visibility: visible;
        }
    }

    @keyframes course-fade-out {
        from{
            left: 0;
            opacity: 1;
            visibility: visible;
        }

        to{
            left: -100%;
            opacity: 0;
            visibility: hidden;
            // position: absolute;
        }
    }
</style>