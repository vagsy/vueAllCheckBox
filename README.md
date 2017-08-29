# vueAllCheckBox
VueJS来实现checkbox的全选和反选

摘要: 1、监听全选的值的变化，来改变checkbox的数组值； 2、监听选择checkbox的数组值的变化，当某一项checkbox有变化，判断是否checkbox的数组长度是否和列表数据的长度一致，来改变全选的值；
html:

<table class="fan-table-permissions">
  <thead>
    <tr>
      <th width="50px"><input type="checkbox" class="fan-checkbox" v-model="checkAll" @click="checkedAll()"></th>
      <th>权限包名</th>
      <th>备注</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="pers in permissionsPackageList">
      <td>
        <input type="checkbox" :value="pers.id" class="fan-checkbox" v-model='ischeckdate' />
      </td>
      <td>{{pers.name}}</td>
      <td>{{pers.remark}}</td>
    </tr>
  </tbody>
</table>
js:

watch:{
 'ischeckdate':function(){
   console.log(this.ischeckdate.toString());
   if(this.permissionsPackageList.length===this.ischeckdate.length){
     this.checkAll=true;
   }else{
     this.checkAll=false;
   }
 },
 checkAll(yes) {
   this.checkAll = yes;
 }
},
 data() {
   return {
     permissionsPackageList:[
       {id:1,name:"BD",remark:"销售"},
       {id:2,name:"导购",remark:"展厅导购"},
       {id:3,name:"HR",remark:"人事"},
     ],
     ischeckdate:[],//获取选项框数据
     checkAll: false,//全选
   }
 },
 methods: {
   checkedAll: function() {
     let ischeckdate = [];
     if (!this.checkAll) {
       this.permissionsPackageList.forEach((item) => {
         ischeckdate.push(item.id);
       });
     }
     this.ischeckdate = ischeckdate;
     console.log("aa-----"+this.ischeckdate.toString());
   },
 }