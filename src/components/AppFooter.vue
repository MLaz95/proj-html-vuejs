<script>
    export default{
        name: 'AppFooter',

        data(){
            return{
                
                    
                courses: [
                    {subject: 'Business English', teacher: 'Preston Marshall'},
                    {subject: 'Social Computing', teacher: 'David Sanders'},
                    {subject: 'Learn Spanish', teacher: 'Jennie King'},
                ],
                
                supportLinks:[
                    'user dashboard', 'contact us', 'FAQ', 'course offer', 'events'
                ]
            }
        }
    }
</script>

<template>
    <footer>
        <div class="container">

            <div class="ft-top">

                <div class="row">
                    <div class="col-3 ft-info">
                        <div class="img-wrapper">
                            <img src="/img/logo-light.png" alt="" class="img-fluid">
                        </div>
                        <p>Providing Life Changes Experiences Through Education. Class That Fit Your Busy Life. Closer To Home</p>
                        <div>
                            <i class="fa-solid fa-phone"></i>
                            <span>1-677-124-44227</span>
                        </div>
                        <div>
                            <i class="fa-regular fa-clock"></i>
                            <span>Mon - Sat 8.00 - 18.00</span>
                        </div>
                    </div>
                    <div class="col-3 ft-info">
                        <h3>Popular Courses</h3>
                        <ul>
                            <li v-for="course in courses">
                                <h4>{{ course.subject }}</h4>
                                <div>{{ course.teacher }}</div>
                            </li>
                        </ul>
                    </div>
                    <div class="col-3 ft-info">
                        <h3>Support</h3>
                        <ul>
                            <li v-for="link in supportLinks">
                                <a href="#!">{{ link }}</a>
                            </li>
                        </ul>
                    </div>
                    <div class="col-3 ft-info">
                        <h3>Flexible Learning</h3>
                        <img src="/img/footer-img-1.png" alt="" class="img-fluid">
                    </div>
                </div>
            </div>

            <div class="ft-bottom row">
                <div>Copyrights 2017 Mikado Themes</div>
                <div class="row ft-contacts">
                    <div>CALL +44 300 303 0266</div>
                    <div>FOLLOW US</div>
                    <i class="fa-brands fa-twitter"></i>
                    <i class="fa-brands fa-instagram"></i>
                    <i class="fa-brands fa-facebook-f"></i>
                </div>
            </div>

        </div>

    </footer>

</template>

<style lang="scss">
    @use '../styles/variables.scss' as *;

    footer{
        padding: 40px;
        color: white;
        background-color: $bg-footer;

        .ft-top{
            border-bottom: 1px solid white; //test
            padding: 100px 0;
        }
        .col-3{
            padding-right: 1rem;
        }

        h3{
            font-size: 1.5rem;
        }

        .img-wrapper{
            width: 140px;
        }

        .ft-info{
            display: flex;
            flex-direction: column;
            gap: 2rem;
        }

        ul{
            list-style: none;
            li{
                padding: 0.5rem 0;
                text-transform: capitalize;
            }

            h4{
                font-size: 1.1rem;
            }
            
            a{
                text-decoration: none;
                color: white;   //test

                &:hover{
                    text-decoration: underline;
                }
            }
        }

        .ft-bottom{
            justify-content: space-between;
            padding-top: 40px;

            .ft-contacts{
                gap: 1rem;
            }
        }
    }
</style>