
<template>
    <div class="box">
        <div class="content">
            <div class="list">
                <div class="item" :class="{active:activeIndex===index}" @click="activeIndex=index"
                     v-for="(item,index) in list" :key="index">
                    {{item.name}}
                </div>
            </div>
            <div class="center-chart">
        <dv-active-ring-chart :config="config" style="width: 370px; height: 370px" />
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                activeIndex:0, //高亮索引
                //数据
                list:[
                    {
                        id:1,
                        name:'1',
                        data:[
                            {
                                name:'1_1',
                                value:255
                            },
                            {
                                name:'1_2',
                                value:124
                            },
                            {
                                name:'1_3',
                                value:557
                            },
                            {
                                name:'1_4',
                                value:224
                            },
                        ]
                    },
                    {
                        id:2,
                        name:'2',
                        data:[
                            {
                                name:'2_1',
                                value:433
                            },
                            {
                                name:'2_2',
                                value:123
                            },
                            {
                                name:'2_3',
                                value:456
                            },
                            {
                                name:'2_4',
                                value:211
                            },
                        ]
                    },
                    {
                        id:3,
                        name:'3',
                        data:[
                            {
                                name:'3_1',
                                value:234
                            },
                            {
                                name:'3_2',
                                value:452
                            },
                            {
                                name:'3_3',
                                value:123
                            },
                            {
                                name:'3_4',
                                value:111
                            },
                        ]
                    },
                    {
                        id:4,
                        name:'4',
                        data:[
                            {
                                name:'4_1',
                                value:222
                            },
                            {
                                name:'4_2',
                                value:333
                            },
                            {
                                name:'4_3',
                                value:411
                            },
                            {
                                name:'4_4',
                                value:211
                            },
                        ]
                    }
                ],
                //图表配置对象
                config:{
                    showOriginValue:true,  //显示具体值
                    //图表显示的数据
                     data: []
                }
            }
        },
        created() {
            this.config.data = this.list[this.activeIndex].data
        },
        watch:{
            activeIndex(){
                this.config = {
                    ...this.config,
                    data:this.list[this.activeIndex].data
                }
            }
        }
    }
</script>

<style lang="scss" scoped>
    .box{
        padding: 10px;
        .title{
            font-size: 15px;
            text-align: center;
        }
        .content{
            display: flex;
            align-items: center;
        }
        .list{
            padding-left: 20px;
            z-index: 2;
            .item{
                margin: 10px 0;
                cursor: pointer;
                background-color: rgba(255,255,255,0.2);
                padding: 4px 10px;
                &.active{
                    background-color: rgba(255,255,255,0.5);
                }
            }
        }
        .center-chart{
            display: flex;
            align-items: center;
            justify-content: center;
            margin-top: 30px;
            margin-left: -50px;
            width: 50%;
            height: 50%;

        }
    }

</style>