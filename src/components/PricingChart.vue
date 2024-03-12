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
    <div class="row price-chart">

        <!-- stub column, the stub info is taken from its own array -->
        <div class="col-3 plan stub">
            <div class="plan-head">
                <h3>Save up to 40% by paying weekly</h3>
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

    </div>

</template>

<style lang="scss">
    @use '../styles/variables.scss' as *;

    .price-chart{
        border-top: 5px solid $border-tertiary;
        padding-bottom: 100px;
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
            align-items: center;
            gap: 1.5rem;
            padding: 45px;
            border: 1px solid $border-primary;
            
            background-color: $bg-fourth;
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

</style>