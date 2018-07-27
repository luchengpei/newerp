<template>
    <div class="look">
        <el-dialog title="查看"
        :visible.sync="show"
        >
            <el-form :model="form">
                <el-form-item label="订单号 :" :label-width="120+'px'">
                    <el-input v-model="form.orderId" auto-complete="off" size="mini"
                    style="width: 190px"
                    placeholder="订单号"
                    ></el-input>
                </el-form-item>
                <el-form-item label="平台 :" :label-width="120+'px'">
                   <el-input v-model="form.site" size="mini" style="width: 190px;" placeholder="平台">

                   </el-input>
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

                </el-form-item>
                <el-form-item label="支付金额 :" :label-width="120+'px'">
                    <el-input v-model="form.sumpay" size="mini" style="width: 190px;" placeholder="支付金额">

                    </el-input>
                </el-form-item>
                <el-form-item label="运输方式 :" :label-width="120+'px'">
                    <el-input v-model="form.transportation" size="mini" style="width: 190px;" placeholder="运输方式">

                    </el-input>
                </el-form-item>
                <el-form-item label="发货仓库" :label-width="120+'px'">
                    <el-input v-model="form.warehouse" size="mini" style="width: 190px;" placeholder="发货仓库">

                    </el-input>
                </el-form-item>
                <el-form-item label="目的地" :label-width="120+'px'">
                    <el-input v-model="form.destination" size="mini" style="width: 190px;" placeholder="平台">

                    </el-input>
                </el-form-item>
                <el-form-item label="跟踪单号" :label-width="120+'px'">
                    <el-input v-model="form.trakingNum" size="mini" style="width: 190px" placeholder="跟踪单号">

                    </el-input>
                </el-form-item>
                <el-form-item label="最迟发货时间" :label-width="120+'px'">
                    <el-input v-model="form.theLastTime" size="mini" style="width: 190px" placeholder="最迟发货时间">

                    </el-input>
                </el-form-item>
            </el-form>
        </el-dialog>
    </div>
</template>

<script>
    export default {
        name: "look",
        props:['tab','row','ls'],
        data() {
            return {
                show:this.ls,
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
                }
            }
        },
        mounted(){
            this.form=this.row
        },
        watch:{
            show(val){
                this.$emit('getstatus',val)
            },
            ls(val){
                this.show=val
            },
            row(val){
                this.form=val
            }
        }
    }
</script>

<style scoped>

</style>