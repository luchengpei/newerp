<template>
    <div class="update">
        <el-dialog title="更新"
                   :visible.sync="show1"
        >
            <el-form :model="form">
                <el-form-item label="订单号 :"
                :label-width="120+'px'"
                >
                    <el-input v-model="form.orderId" size="mini"
                              style="width: 190px;"
                              placeholder="请输入订单号"
                              @change="change"
                    >

                    </el-input>
                </el-form-item>
                <el-form-item label="站点" :label-width="120+'px'">
                    <el-select size="mini" v-model="form.site" placeholder="请输入站点">
                        <el-option v-for="(item,index) in formarr" :key="index" :value="item.value" :label="item.label">

                        </el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="账号简称 :" :label-width="120+'px'">
                    <el-input v-model="form.account" size="mini" style="width: 190px;" placeholder="账号">

                    </el-input>
                </el-form-item>
                <el-form-item label="买家ID :" :label-width="120+'px'">
                    <el-input v-model="form.shopId" size="mini" style="width: 190px;" placeholder="买家">

                    </el-input>
                </el-form-item>
                <el-form-item label="销售员 :" :label-width="120+'px'">
                    <el-input v-model="form.sale" size="mini" style="width: 190px;" placeholder="销售员">

                    </el-input>
                </el-form-item>
                <el-form-item label="付款状态 :" :label-width="120+'px'">
                    <el-input v-model="form.paymentstatus" size="mini" style="width: 190px;" placeholder="yes or no">

                    </el-input>
                </el-form-item>
                <el-form-item label="支付金额 :" :label-width="120+'px'">
                    <el-input v-model="form.sumpay" size="mini" style="width: 190px;" placeholder="支付金额">

                    </el-input>
                </el-form-item>
                <el-form-item label="运输方式 :" :label-width="120+'px'">
                   <el-select v-model="form.transportation" size="mini" placeholder="请选择运输方式">
                       <el-option v-for="(item,index) in option" :key="index" :value="item.value" :lable="item.label">

                       </el-option>
                   </el-select>
                </el-form-item>
                <el-form-item label="发货仓库" :label-width="120+'px'">
                    <el-select v-model="form.warehouse" placeholder="请选择仓库" size="mini">
                        <el-option v-for="(item,index) in formwarnhouse" :key="index" :value="item.value" :label="item.label">

                        </el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="目的地" :label-width="120+'px'">
                    <el-input v-model="form.destination" size="mini" style="width: 190px;" placeholder="平台">

                    </el-input>
                </el-form-item>
                <el-form-item label="跟踪单号" :label-width="120+'px'">
                    <el-input v-model="form.trakingNum" size="mini" style="width: 190px" placeholder="跟踪单号">

                    </el-input>
                </el-form-item>
                <!--<el-form-item label="最迟发货时间" :label-width="120+'px'">-->
                    <!--<el-input v-model="form.theLastTime" size="mini" style="width: 190px" placeholder="最迟发货时间">-->

                    <!--</el-input>-->
                <!--</el-form-item>-->
            </el-form>
        </el-dialog>

    </div>
</template>

<script>
    export default {
        name: "test",
        props:['table1','testshow1'],
        data() {
            return {
                obj:{},
                show1:this.testshow1,
                form:{
                    orderId:'',
                    sumpay:'',
                    sale:'',
                    shopId:'',
                    account:'',
                    site:'',
                    transportation:'',
                    destination:'',
                    warehouse:'',
                    theLastTime:'',
                    trakingNum:'',
                    paymentstatus:''
                    },
                    formarr:[
                        {
                            value:'亚马逊',
                            label:'亚马逊'
                        },
                        {
                            value:'ebay',
                            label:'ebay'
                        },
                        {
                            value:'谁知道啊',
                            label:'谁知道啊'
                        }
                    ],
                    option:[
                        {
                            value:'海运',
                            label:'海运'
                        },
                        {
                            value:'中通',
                            label:'中通'
                        },
                        {
                            value:'顺丰',
                            label:'顺丰'
                        },
                        {
                            value:'空运',
                            label:"空运"
                        }
                    ],
                    formwarnhouse:[
                        {
                            value:'本地仓',
                            label:'本地仓'
                        },
                        {
                            value:'海外仓',
                            label:'海外仓'
                        },
                        {
                            value:'中山仓',
                            label:"中山仓"
                        }
                    ]

            }
        },
        methods: {
            change() {
                console.log(this.form.orderId)
            },
            getpaymentstatus(){
                let num= ''
                for(var i=0;i<2;i++){
                    num+=Math.floor(Math.random()*2)
                }
                if(num%2==0){
                    console.log(num)
                    return 'yes'
                }else {
                    return 'no'
                }
            }
        },
        updated(){
            //更新   而不用mouted mouted挂摘 这里的到的动态值 是没有 比如我想要的table1
            //所以 点击的时候会带进了 table1 因为我是动态绑定的table1 我在table组件里面点击想app触发时间 得到动态的
            //这里的table1的值
            this.form=this.table1
        },
        watch:{//监听父组件传来的原始test的状态值 因为 这个值 在table组件里面已经 改变了
            testshow1(val){
                this.show1=val
            },
            show1(val){//监听本组件动态改变传来的原始值  即show1 通过事件给父组件的原始值等于新的值
                this.$emit('getshow',val)
            }
        }
    }
</script>

<style scoped>

</style>