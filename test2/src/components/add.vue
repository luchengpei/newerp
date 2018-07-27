<template>
        <div>
            <el-dialog title="更新"
                       :visible.sync="show"
            >
                <el-form :model="form">
                    <el-form-item label="订单号 :"
                                  :label-width="120+'px'"
                    >
                        <el-input v-model="form.orderId" size="mini"
                                  style="width: 190px;"
                                  placeholder="请输入订单号"
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
                </el-form>
                <div class="btns">
                    <el-button type="success" size="mini" @click="adddata">添加</el-button>
                    <el-button  size="mini" @click="cancle">取消</el-button>
                </div>
            </el-dialog>
        </div>
</template>

<script>
    export default {
        name: "add",
        props:['value','addshow'],
        data() {
            return {
                tab:this.value,
                show: this.addshow,
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
                    paymentstatus:'',
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
            cancle(){
                this.show=false
            },
            adddata(){
               let order= this.form.orderId.length
               let sumpay=this.form.sumpay.length
               let sale=this.form.sale.length
               let shopid=this.form.shopId.length
               let account=this.form.account.length
               let site= this.form.site.length
               let trans= this.form.transportation.length
               let des= this.form.destination.length
               let ware = this.form.warehouse.length
               let tra = this. form.trakingNum.length
               let paysum= this.form.paymentstatus.length
                if(order==0 || sumpay==0 || sale==0 ||shopid==0 || account==0 ||site==0 || trans==0 || des==0 ||ware==0 ||tra==0 ||paysum==0){
                   this.$message('请输入更新内容')
                }else {
                   this.form.theLastTime=new Date().toLocaleDateString()
                   this.tab.unshift(this.form)
                   this.cancle()
                }
            }
        },
        watch:{
            show(val){
                this.$emit('getadd',val)
            },
            addshow(val){
                this.show=val
            }
        }
    }
</script>

<style scoped>
.btns{
    margin-left: 500px;
}
</style>