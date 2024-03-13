<script>
    export default{
        name: 'BenefitTabs',

        data(){
            return{
                benefitsArray:[
                    {
                        name: 'What We Do',
                        title: 'Learning Possibilities',
                        text: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Modi quisquam quos, enim recusandae, libero officiis nobis culpa earum perferendis dicta odio temporibus, reiciendis explicabo eos quasi? Maiores quod assumenda saepe?',
                        list: ['We enrich lives thorugh learning.', 'Maximizing potential thorugh individual attention', 'The trusted name for specialized traning.', 'People teach. People learn. This is where they connect'],
                        imgPath: '/img/h12-tabs-icon-1.png'
                    },{
                        name: 'Degree Programme',
                        title: 'Title 2',
                        text: 'Maecenas eget vulputate purus, id suscipit justo. Duis eu convallis nisl, eget luctus nibh. Vivamus accumsan pharetra quam eu euismod. Etiam ultricies egestas varius. Proin eget scelerisque lacus.',
                        list: ['longer sample text', 'sample text', 'much longer sample text', 'sample text'],
                        imgPath: '/img/h12-tabs-icon-2.png'
                    },{
                        name: 'Career Achievements',
                        title: 'Title 3',
                        text: 'Curabitur tortor est, maximus at rhoncus eget, tincidunt ac mi. In hac habitasse platea dictumst. Curabitur ultricies diam dolor, id iaculis arcu consequat vitae.',
                        list: ['sample text', 'much longer sample text', 'longer sample text', 'sample text'],
                        imgPath: '/img/h12-tabs-icon-3.png'
                    },{
                        name: 'Personal Management',
                        title: 'Title 4',
                        text: 'Mauris eget lobortis erat, quis congue leo. Phasellus pretium magna eget risus pretium cursus. Integer in blandit ipsum. Integer id lacus et nisl varius hendrerit.',
                        list: ['sample text', 'longer sample text', 'sample text', 'much longer sample text'],
                        imgPath: '/img/h12-tabs-icon-4.png'
                    },{
                        name: 'Knowledge Transfer',
                        title: 'Title 5',
                        text: 'Cras eget suscipit dui, id congue massa. Proin nibh nunc, vestibulum vel lacus sed, euismod porttitor risus. Curabitur a facilisis quam, vel hendrerit odio.',
                        list: ['sample text', 'longer sample text', 'much longer sample text', 'sample text'],
                        imgPath: '/img/h12-tabs-icon-5.png'
                    },
                ],

                activeTab: 0,
            }
        }
    }
</script>

<template>
    <div id="benefits" class="container">
        <aside>
            <ul>
                <li
                    v-for="(obj, index) in benefitsArray"
                    :class="{active: index == activeTab}"
                    @click="activeTab = index"
                    >{{ obj.name }}
                </li>
            </ul>
        </aside>
        <main>
            <h2>{{ benefitsArray[activeTab].title }}</h2>
            <p>{{ benefitsArray[activeTab].text }}</p>
            <ul>
                <li v-for="item in benefitsArray[activeTab].list">{{ item }}</li>
            </ul>
            <img :src="benefitsArray[activeTab].imgPath" alt="">
        </main>
    </div>

</template>


<style lang="scss">
    @use '../styles/variables.scss' as *;

    #benefits{
        padding: 120px 0;
        display: flex;
    
        aside{
            flex: 0 0 270px;
            border:  1px solid $border-primary;
            border-bottom: none;

            ul{
                list-style: none;

                li{
                    padding: 30px;
                    border-bottom: 1px solid $border-primary;
                    font-weight: bold;
                    position: relative;

                    &:hover{
                        cursor: pointer;
                        background-color: $bg-fifth;
                    }

                    &.active{
                        color: $bg-primary;
                        background-color: $bg-fifth;

                        &::before{
                            content: '';
                            width: 10px;
                            height: 100%;
                            background-color: $bg-primary;
                            position: absolute;
                            top: 0;
                            left: 0;
                        }
                    }
                }
            }
        }

        main{
            flex-grow: 1;
            padding: 30px 45px 0;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            position: relative;

            border: 1px solid $border-primary;
            border-left: none;

            ul{
                list-style: none;
                
                li{
                    line-height: 2rem;
                    &::before{
                        content: '\2713';
                        color: $bg-primary;
                        padding-right: 0.5rem;
                    }
                }
            }

            p{
                font-size: 18px;
                line-height: 1.5rem;
            }

            img{
                width: 110px;
                position: absolute;
                right: 45px;
                bottom: 0;
            }
        }
    }
</style>