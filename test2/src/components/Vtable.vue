<template>
    <div class="table">
        <el-table :data="initdata()"
        style="width: 100%"
        :default-sort="{prop:'date',order:'descending'}"
        border
        >
        <el-table-column
        prop="orderId"
        label="订单号"
        width="180"
        align="center"
        >

        </el-table-column>
        <el-table-column
        prop="site"
        label="平台/站点"
        width="100"
        align="center"
        >

        </el-table-column>
        <el-table-column
        prop="account"
        label="账号简称"
        width="100"
        align="center"
        >

        </el-table-column>
        <el-table-column
        prop="shopId"
        label="买家ID"
        width="100"
        align="center"
        >

        </el-table-column>
        <el-table-column
        prop="sale"
        label="销售员"
        width="100"
        align="center"
        >

        </el-table-column>
        <el-table-column
        prop="paymentstatus"
        label="付款状态"
        sortable
        width="100"
        align="center"
        >

        </el-table-column>
        <el-table-column
        prop="sumpay"
        label="支付金额"
        sortable
        width="100"
        align="center"
        >

        </el-table-column>
        <el-table-column
        prop="transportation"
        label="运输方式"
        width="100"
        align="center"
        >

        </el-table-column>
        <el-table-column
        prop="warehouse"
        label="发货仓库"
        width="100"
        align="center"
        >

        </el-table-column>
        <el-table-column
        prop="destination"
        label="目的地"
        width="100"
        sortable
        >

        </el-table-column>
        <el-table-column
        prop="trakingNum"
        label="跟踪单号"
        width="100"
        align="center"
        >

        </el-table-column>
        <el-table-column
        prop="theLastTime"
        label="最迟发货时间"
        width="120"
        sortable
        align="center"
        >

        </el-table-column>
        <el-table-column
        label="操作"
        width="180"
        align="center"
        >
        <template slot-scope="scope">
            <el-button type="text" size="mini" @click="check(scope.row)">
                查看
            </el-button>
            <el-button type="text" size="mini" @click="edit(scope.row)">
                编辑
            </el-button>
            <el-button type="text" size="mini" @click="add">
                添加
            </el-button>
            <el-button type="text" size="mini" @click="hahadelete(scope.$index,tableData,scope.row)">
                删除
            </el-button>
        </template>
        </el-table-column>
        </el-table>
    </div>
</template>

<script>
    export default {
        name: "Vtable",
        props:['table','search','tab','value','lookto','testshow1','addshow1'],
        data(){
            return {
                changelook:false,
                newvalue:false,
                editshow:false,
                addshow:false,
                tableData:[
                    {
                        orderId:'111',
                        site:'亚马逊',
                        account:'mine',
                        shopId:'1',
                        sale:'某某某',
                        paymentstatus:'yes',
                        sumpay:'100',
                        transportation:'海运',
                        warehouse:'本地仓',
                        destination:'深圳',
                        trakingNum:'1548',
                        theLastTime:new Date().toLocaleDateString()
                    },
                    {
                        orderId:'222',
                        site:'ebay',
                        account:'your',
                        shopId:'2',
                        sale:'某xx',
                        paymentstatus:'no',
                        sumpay:'1000',
                        transportation:'中通',
                        warehouse:'海外仓',
                        destination:'广州',
                        trakingNum:'1548',
                        theLastTime:new Date().toLocaleDateString()
                    },
                    {
                        orderId:'454584878748',
                        site:'ebay',
                        account:'what the fuck',
                        shopId:'2',
                        sale:'我只是个菜逼',
                        paymentstatus:'no',
                        sumpay:'1000',
                        transportation:'顺丰',
                        warehouse:'海外仓',
                        destination:'茂名',
                        trakingNum:'1548',
                        theLastTime:new Date().toLocaleDateString()
                    },
                    {
                        orderId:'45458488',
                        site:'谁知道啊',
                        account:'exm?',
                        shopId:'2',
                        sale:'vue好像好屌啊',
                        paymentstatus:'yes',
                        sumpay:'1000',
                        transportation:'海运',
                        warehouse:'中山仓',
                        destination:'茂名信宜',
                        trakingNum:'148',
                        theLastTime:new Date().toLocaleDateString()
                    },
                    {
                        orderId:'110',
                        site:'亚马逊',
                        account:'your father',
                        shopId:'2',
                        sale:'ng也想学',
                        paymentstatus:'gg',
                        sumpay:'1000',
                        transportation:'中通',
                        warehouse:'本地仓',
                        destination:'深圳北站',
                        trakingNum:'148',
                        theLastTime:new Date().toLocaleDateString()
                    },
                    {
                        orderId:'119',
                        site:'ebay',
                        account:'your mother',
                        shopId:'10',
                        sale:'react也想学',
                        paymentstatus:'yes',
                        sumpay:'999',
                        transportation:'空运',
                        warehouse:'本地仓',
                        destination:'广州南',
                        trakingNum:'148',
                        theLastTime:new Date().toLocaleDateString()
                    },
                    {
                        orderId:'10086',
                        site:'谁知道啊',
                        account:'桑榆未晚',
                        shopId:'88',
                        sale:'微信小程序也想学啊',
                        paymentstatus:'yes',
                        sumpay:'999',
                        transportation:'顺丰',
                        warehouse:'本地仓',
                        destination:'广西桂林',
                        trakingNum:'198',
                        theLastTime:new Date().toLocaleDateString()
                    },
                ]
            }
        },
        methods: {
            // formatter(row,col) {
            // },
            initdata(){
                if(this.tab.length==0) {
                    // console.log(111)
                    return this.tableData
                }
                return this.tab
            },
            hahadelete(index,tablist,row){
                this.newvalue=true
                this.$emit('input',this.newvalue,index,tablist,row)
            },
            check(row){
                this.changelook=true
                this.$emit('check',row,this.changelook)
            },
            //改变父组件传来的test的状态
            edit(row){
                // console.log(this.editshow)
                this.editshow=true
                this.$emit('edit',row)
            },
            add(){
                this.addshow=true
            }
        },
        watch:{
           changelook(val){

           },
            //监听test的dialogshow的状态
            editshow(val){
                this.$emit('gettestshow',this.editshow)
            },
            testshow1(val){
               this.editshow=val
            },
            //监听test的dialog的状态
            addshow(val){
               this.$emit('getaddshow',val)
            },
            addshow1(val){
               this.addshow=val
            }
        },
        mounted(){
            // console.log(this.table)
            this.$emit('update:table',this.tableData)
        },
        // computed:{
        //     change(){
        //         // console.log(this.search)
        //         if(this.search=='全部') {
        //             return this.tableData
        //         }else if(this.search==''){
        //             return this.tableData
        //         }
        //         return this.tableData.filter(k=>{
        //             return k.site==this.search
        //         })
        //         this.search=''
        //     }
        // }
    }
</script>

<style scoped>

</style>