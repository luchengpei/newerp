<template>
    <div class="button">
        <el-dropdown split-button type="primary" @command="handleSelect" size="mini">
            {{data}}
            <el-dropdown-menu slot="dropdown">
                <el-dropdown-item command="部分导出">
                    部分导出
                </el-dropdown-item>
                <el-dropdown-item command="全部导出">
                    全都导出
                </el-dropdown-item>
            </el-dropdown-menu>
        </el-dropdown>
    </div>
</template>

<script>
    export default {
        name: "Vbutton",
        data() {
            return {
                data: '导出'
            }
        },
        methods: {
            handleSelect(command) {
               this.data=command
            }
        },
    }
</script>

<style scoped>
.button{
    margin: 10px 0;
}
</style>