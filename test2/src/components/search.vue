<template>
    <div class="search">
        <el-row>
            <span>平台 ：</span>
            <el-select placeholder="全部" v-model="values.value1" size="mini" @change="change(values.value1)">
                    <el-option v-for="(item,index) in station" :key="item.value1"
                    :label="item.label"
                     :value="item.value1"
                    >
                    </el-option>
            </el-select>
            <span>站点 ：</span>
            <el-select placeholder="请选择平台" v-model="values.value2" size="mini" :disabled="select">
                <el-option v-for="(item,index) in site" :key="item.value2"
                :label="item.label"
                :value="item.value2"
                >

                </el-option>
            </el-select>
            <span>账号简称 ：</span>
            <el-select v-model="values.value2" placeholder="请先选择站点" size="mini" :disabled="select">
                <el-option v-for="(item,index) in site" :key="item.value2"
                :label="item.label"
                :value="item.value2"
                >

                </el-option>
            </el-select>
            <span>发货仓库 ：</span>
            <el-select size="mini" placeholder="全部" v-model="values.value3">
                <el-option v-for="(item,index) in warehouse"
                :key="item.value3"
                :label="item.label"
                :value="item.value3"
                >

                </el-option>
            </el-select>
            <span>运输方式 :</span>
            <el-select size="mini" placeholder="请选择发货仓库" v-model="values.value4" :disabled="select">
                <el-option v-for="(item,index) in transportation" :key="item.value4"
                :label="item.label"
                :value="item.value4"
                >

                </el-option>
            </el-select>
        </el-row>
    </div>
</template>

<script>
    export default {
        name: "Search",
        props:['search'],
        data(){
            return {
                select:true,
                values:{
                  value1:'',
                  value2:'',
                  value3:'',
                  value4:''
                },
                station:[
                    // {
                    //     value1:'全部',
                    // },
                    {
                        value1:'全部',
                        lable:'全部'
                    },
                    {
                        value1:'亚马逊',
                        label:'亚马逊'
                    },{
                        value1:'ebay',
                        label:'ebay'
                    },
                    {
                        value1:'谁知道啊',
                        label:'谁知道啊'
                    }

                ],
                site:[
                    {
                        value2:'美国',
                        lable:'美国'
                    },
                    {
                        value2:'英国',
                        lable:'英国'
                    },
                    {
                        value2:'中国',
                        label:'中国'
                    }
                ],
                warehouse:[
                    {
                        value3:'本地仓',
                        label:'本地仓'
                    },
                    {
                        vlaue3:'海外仓',
                        label:'海外仓'
                    },
                    {
                        vlaue3:'中山仓',
                        label:'中山仓'
                    }
                ],
                transportation:[
                    {
                        value4:'海运',
                        label:'海运'
                    },
                    {
                        value4:'空运',
                        label:'空运'
                    },
                    {
                        value4:'顺丰',
                        label:'顺丰'
                    },
                    {
                        vlaue4:'中通',
                        label:'中通'
                    }
                ]
            }
        },
        methods: {
            change(val) {
              this.select=false
              this.$nextTick(function () {
                  this.$emit('update:search',this.values)
              })
            }
        },
    }
</script>

<style scoped>

</style>