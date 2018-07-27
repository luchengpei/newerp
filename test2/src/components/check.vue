<template>
    <div class="check">
        <el-row>
            <el-select size="mini" placeholder="订单号" v-model="value">
                    <el-option :value="orderId[0].value">
                        <template>
                            <span scope="slot scope">{{orderId[0].label}}</span>
                        </template>
                    </el-option>
            </el-select>
            <el-input size="mini" v-model="value1" placeholder="可批量搜索，Shift+回车换行..." style="width: 200px">

            </el-input>
            <span>所属类型 ：</span>
            <el-select size="mini" placeholder="全部" v-model="value2">

            </el-select>
            <span>销售员</span>
            <el-autocomplete style="width: 120px" size="mini" placeholder="可输入搜索" v-model="value3"
            class="inline-input"
            :fetch-suggestions="querySearch"
             @select="handlerSelect"
            >

            </el-autocomplete>
            <el-select placeholder="下单时间" size="mini" v-model="value4" style="width: 100px">
                下单时间
            </el-select>
            <el-date-picker type="date" v-model="value5" placeholder="开始时间" size="mini" :picker-options="startSelect">

            </el-date-picker>
            <span>--</span>
            <el-date-picker type="date" v-model="value6" placeholder="结束时间" size="mini"  :picker-options="endSelect">

            </el-date-picker>
            <el-button type="primary" size="mini" @click="searchdata">搜索</el-button>
            <el-button  disabled size="mini" style="height: 28px;background: #ddd">还原修改</el-button>
            <el-button size="mini" type="warning" @click="clear">清空条件</el-button>
        </el-row>
        <el-row>
            <!--{{change}}{{table}}-->
        </el-row>
    </div>
</template>

<script>
    export default {
        name: "Check",
        props:['data','table'],
        data(){
            return {
                value:'',
                value1:'',
                value2:"",
                value3:"",
                value4:'',
                value5:'',
                value6:"",
                arrdata:[],
                orderId:[
                    {
                        value:'订单号',
                        label:'订单号'
                    }
                ],
                startSelect:{
                    disabledDate:(time)=>{
                        return time.getTime()>Date.now()
                    }
                },
                endSelect:{
                    disabledDate:(time)=>{
                       if(this.value5){
                           return time.getTime()<new Date(this.value5).getTime() || time.getTime()>Date.now()
                       }
                       return time.getTime()>Date.now()
                    }
                }
            }
        },
        methods: {
                querySearch(querydata,callback) {
                    var arrdata=this.arrdata
                    var res = querydata?arrdata.filter(this.createFilter(querydata)):arrdata
            },
            createFilter(querydata){
                   return(arr)=>{
                       return (arr.value.toLocaleLowerCase().indexOf(querydata.toLocaleLowerCase())===0)
                   }
            },
            handlerSelect(item){
                    console.log(item)
            },
            searchdata(){
                this.$emit('getdata',this.change)
            },
            clear(){
                  this.value=''
                  this.value1=''
                  this.value2=''
                  this.value3=''
                  this.value4=''
                  this.value5=''
                  this.value6=''
                  this.data.value1=''
                  this.data.value2=''
                  this.data.value3=''
                  this.data.value4=''
            }
        },
        computed:{
            change(){
                if(JSON.stringify(this.data)=="{}"){
                    return this.table
                }
                // else if(this.data==''){
                //     return this.table
                // }
                return this.table.filter(k=>{
                    return k.site==this.data.value1 ||k.transportation==this.data.value4
                })

            }
        }

    }
</script>

<style scoped>

</style>