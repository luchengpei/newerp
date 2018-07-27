<template>
  <div id="app">
      <Search :search.sync="search" >

      </Search>
      <Check :data="search" :table="tabledata" @getdata="getdata">

      </Check>
      <Vbutton ></Vbutton>
    <Vtable :table.sync="tabledata" :search="search" :tab="newTabledata" v-model="newcancle" @input="input" @check="check" :lookto="looks" @edit="edit1" :testshow1="testshow"
    @gettestshow="gettestshow"
    :addshow1="addshow"
    @getaddshow="getaddshow"
    >

    </Vtable>
    <clearDialog  v-model="newcancle" :table="tabledata" :index="deleteindex" :deletedatalist="deletedata">

    </clearDialog>
      <Look :tab="tabledata" :row="rowobj" :ls="looks" @getstatus="getstatus"> </Look>
      <test @getlist="getlist" :table1="edittable" @getshow="getshow" :testshow1="testshow"></test>
      <add v-model="tabledata" @getadd="getadd" :addshow="addshow"></add>
  </div>
</template>

<script>
  import Search from "@/components/search"
  import Check from '@/components/check'
  import  Vtable from '@/components/Vtable'
  import  Vbutton from '@/components/Vbutton'
  import  clearDialog from '@/components/clearDialog'
  import  Look from '@/components/look'
  import  test from '@/components/test'
  import  add from '@/components/add'
export default {
  name: 'App',
    data() {
        return {
            search: {},
            tabledata:[],
            newTabledata:[],
            // initvalue:{},
            // cancle:false,
            newcancle:false,
            deletedata:[],
            deleteindex:0,
            rowobj:{},
            looks:false,
            listdata:{},
            edittable:{},
            testshow:false, //test的原始状态,
            addshow:false,
        }
    },
    watch:{
      cancle(val){
        this.newcancle=val
      },
        /*
        * 只有父组件里面自己动态改变值得时候 才需要监听  这里没用到
        * */
        // looks(val){
        //   this.looks=val
        // },
        // testshow(val){
        //   this.testshow=val
        // }
    },
    methods: {
        getdata(val) {
            this.newTabledata=val
        },
        input(buerzhi,index,tablist,row){
            this.deletedata=tablist
            this.deleteindex=index
            // console.log(this.rowobj)
        },
        check(val,look){
            this.rowobj=val
            this.looks=look
        },
        getstatus(val){
            this.looks=val
        },
        getlist(val){
            this.listdata=val
            this.tabledata.push(this.listdata)
        },
        edit1(val){
            this.edittable=val
            //console.log(this.edittable)
        },
        getshow(val){
            this.testshow=val
        },
        gettestshow(val){//这是事件来获取动态的原始的test值在table组件里的变化的时候
            this.testshow=val
        },
        getadd(val){
            this.addshow=val
        },
        getaddshow(val){
            this.addshow=val
        }
    },
  components:{
     Search,
     Check,
      Vtable,
      Vbutton,
      clearDialog,
      Look,
      test,
      add

  }

}
</script>

<style>

</style>
