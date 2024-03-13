<script>
    export default{
        name: 'PricingChart',

        data(){
            return{
                plans:[
                    {
                        imgPath: '/img/h5-custom-icon-7.png',
                        name: 'Standard',
                        cost: 12,
                        perks:{
                            numberCourses: 2,
                            time: '15 Days',
                            web: true,
                            design: true,
                            marketing: false,
                            python: false,
                            android: false,
                            business: false,
                        }
                    },{
                        imgPath: '/img/h5-custom-icon-8.png',
                        name: 'Professional',
                        cost: 59,
                        perks:{
                            numberCourses: 4,
                            time: '30 Days',
                            web: true,
                            design: true,
                            marketing: true,
                            python: true,
                            android: false,
                            business: false,
                        }
                    },{
                        imgPath: '/img/h5-custom-icon-9.png',
                        name: 'Advanced',
                        cost: 88,
                        perks:{
                            numberCourses: 6,
                            time: '30 Days',
                            web: true,
                            design: true,
                            marketing: true,
                            python: true,
                            android: true,
                            business: true,
                        },
                    }
                ],

                keyList:[
                    'Number of Courses',
                    'Time',
                    'Web Design',
                    'Human-Centered-Design',
                    'Basic Marketing',
                    'Python for Everybody',
                    'Android Developer',
                    'Business English',
                ],

                activeColumn: 1,
            }
        },
    }
</script>

<template>
    <div class="row price-chart container">
        <!-- stub column, the stub info is taken from its own array -->
        <div class="col-3 plan stub">
            <div class="plan-head">
                <h3><strong>Save up to 40% by paying weekly</strong></h3>
            </div>
            <div v-for="item in keyList" class="plan-cell">{{ item }}</div>
        </div>

        <!-- adds a column for each plan -->
        <div class="col-3 plan" v-for="(plan, index) in plans" :class="{active: activeColumn == index}">
            <div class="plan-head">
                <img :src="plan.imgPath" alt="">
                <h3>{{ plan.name }}</h3>
                <div><strong>${{ plan.cost }}</strong></div>
            </div>

            <!-- adds a cell beneath that columns for each item in the perks list -->
            <div v-for="item in plan.perks" class="plan-cell">
                <div v-if="item == true" class="check">&check;</div>
                <div v-else-if="item == false">&#10007;</div>
                <div v-else>{{ item }}</div>
            </div>
            
            <!-- purchase button at the end -->
            <div class="plan-cell btn">
                <button :class="{active: activeColumn == index}" @click="activeColumn = index">Get it Now</button>
            </div>
        </div>
        
        <div class="side-buttons">
            <!-- qode -->
            <button><img src="/img/qode-icon.png" alt="qode"></button>
            <!-- cart -->
            <button><i class="fa-solid fa-cart-shopping"></i></button>
        </div>
    </div>

</template>

<style lang="scss">
    @use '../styles/variables.scss' as *;

    .price-chart{
        border-top: 5px solid $border-tertiary;
        padding-bottom: 50px;
        position: relative;
        background-color: white;
    }
    .plan{
        display: flex;
        flex-direction: column;
        position: relative;

        &.active::before{
            content: '';
            width: 100%;
            height: 5px;
            background-color: $bg-primary;
            position: absolute;
            top: -5px;
            left: 0;

        }

        &.stub{
            text-align: start;
        }

        .plan-head{
            height: 260px;
            display: flex;
            flex-direction: column;
            justify-content: end;
            align-items: center;
            gap: 1.5rem;
            padding: 45px;
            border: 1px solid $border-primary;
            
            background-color: $bg-fourth;

            h3 strong{
                font-size: 1.4rem;
            }
        }

        .plan-cell{
            height: 60px;
            padding: 1rem;
            border: 1px solid $border-primary;

            .check{
                color: $bg-primary;
                font-weight: bold;
            }

            &.btn{
                background-color: $bg-fourth;
                height: auto;

                button{
                    padding: 0.5rem 1rem;
                    font-size: 0.7rem;
                    font-weight: bold;
                    text-transform: uppercase;
                    background-color: white;
                    border: 1px solid $border-primary;

                    &:hover, &.active{
                        cursor: pointer;
                        background-color: $bg-primary;
                        border: 1px solid $bg-primary;
                        color: white;
                    }
                }
            }
        }
    }

    .side-buttons{
        // z-index: -1;

        button{
            cursor: pointer;
            position: absolute;
            left: calc(100% - 2px);
            z-index: 10;

            width: 42px;
            height: 42px;
            color: #EE2852;
            background-color: white;
            border: none;
            box-shadow: 3px 0 10px rgba($color: #000000, $alpha: 0.2);
            transition: width 0.3s, height 0.3s;
            
            img{
                width: 42px;
            }

            &:first-child{
                top: 20px;
            }

            &:nth-child(2){
                top: 70px;
            }

            &:hover{
                width: 80px;
            }
        }
    }

    @media screen and (max-width: 1024px) {
        .side-buttons{
            

            button:first-child{
                left: calc(90% - 50px);
                bottom: calc(100% + 4px);
                top: auto;

                &:hover{
                    height: 80px;
                    width: 42px;
                }
            }

            button:nth-child(2){
                left: 90%;
                bottom: calc(100% + 4px);
                top: auto;

                &:hover{
                    height: 80px;
                    width: 42px;
                }
            }
        }
    }

</style>