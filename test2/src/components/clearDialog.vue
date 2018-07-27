<template>
    <div class="cleardialog">
        <el-dialog
                width="30%"
                title="真的要删除？"
                :visible.sync="value"
                center
               >
            <span>真的要删除？sure？想清楚点</span>
            <div slot="footer">
                <el-button type="danger" size="mini" @click="sure">删除</el-button>
                <el-button type="" size="mini" @click="cancle1">取消</el-button>
            </div>
        </el-dialog>
    </div>
</template>

<script>
    export default {
        name: "clearDialog",
        props:['value','table','index','deletedatalist'],
        data() {
            return {
                cancle2: this.value,
                delindex:this.index,
                deltab:this.deletedatalist,
                datainit:this.table
            }
        },
        methods: {
            cancle1() {
                this.cancle2=false
                this.$emit('input',this.cancle2)
            },
            sure(){
                  this.deltab.splice(this.delindex,1)
                  this.cancle1()
            }
        },
        watch:{
            value(val){
                this.$emit('input',val)
            },
            index(val){
                this.delindex=val
            },
            deletedatalist(val){
                this.deltab=val
            }
        },
        computed:{
            dykey(){
                return this.deltab
            }
        }
    }
</script>

<style scoped>

</style>