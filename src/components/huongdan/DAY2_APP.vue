<!-- Code logic js -->
<script setup>
//c1: option api
//c2 : composition api: dùng ref, reactive
import{ ref, reactive}from "vue";
//1. dùng ref với kiểu dữ liệu nguyên thuỷ
let count = ref(0);
let studentName= ref('FE Framework vue 3');
let studentEmail = ref("thaiinguyenn20112006@gmail.com");
let studentAge= ref(18);
let studentIsActive = ref(true);
//2. dùng rea tive với kiểu dữ liệu đối tượng
let state= reactive({ amount:0, name:'abc', status:false});
//C1: viết hàm
function IncreamentCount(){
    //tăng giá trị của count
    count.value++;
}
console.log(state);
const IncreamentAmount =()=>{
state.amount++;
}
//way  dât binding
let hovaten= ref("Nguyễn Doanh Thái");

const onClickDangKy=()=>{
    alert("Đăng ký thành công");
}
const onBlurInput=()=>{
    alert("Gọi hàm onBlurInputr")
}
//style binding
let styleString = 'font-size:20px; color:red';
// property binding
let logoUrl ='/img/Logo.jpg';
//đường dẫn trực tiếp
let cauNoiYeuThich="suýt trượt môn"
</script>
<!-- viết code html -->
<template>
    <h1>Thông tin</h1>
    <ul class="list-group">
        <li class="list-group-item">Tên sinh viên:{{ studentName }}</li>
        <li class="list-group-item">Email:{{ studentEmail }}</li>
        <li class="list-group-item">Tuổi:{{ studentAge }}</li>
        <li class="list-group-item">
            Trạng Thái:{{ studentIsActive ? 'Đang học' :'Đang bảo lưu' }}
        </li>
    </ul>
    <!-- EVENT BINDING -->
   COUNT:{{ count }}
   <button class="btn btn-primary" @click="IncreamentCount">Increament count</button>
   <!-- hiện thị giá trị thuộc tính của dối tượng:[Tên đối tượng].[tên thuộc tính] -->
    AMOUNT:{{ state.amount }}
    <button class="btn btn-success"@click="IncreamentAmount">Increament amount</button>
    <hr>
    <h3>2 way data binding</h3>
    <p>sử dụng đồng bộ dữ liệu từ code js và html</p>
    <div>
        <label for="" class="form-label"></label>
        <input type="text" name="form-control" v-model="hovaten">
        <p>Xin chào{{ hovaten }}</p>
    </div>
    <hr>
    <h3>Event binding</h3>
    <p>Sử dụng  để bắt đầu sự kiện người dùng tương tác với html</p>
    <div>
        <h6>BẮt sự kiện click</h6>
        <button class="btn btn-primary" @click="onClickDangKy">Đăng ký</button>
        <h6>Bắt sự kiện blur</h6>
        <input type="text" class="form-control"@blur="onBlurInput()">
    </div>
    <hr>
    <h3>class binding</h3>
    <p>v-binding:class dùng để binding các lớp css cho 1 phần tử</p>
    <p>Class binding -Chuỗi</p>
    <div v-bind:class="'active'">
        {{ hovaten }}
    </div>
    <p>Class binding -Đối tượng</p>
    <div :class="{active: state.amount >=1}">
        {{ state.amount }}
    </div>
    <!-- Style binding -->
     <hr>
     <h3>STYLE BINDING</h3>
     <p>style chuỗi, đối tượng, điều kiện</p>
     <div :style="styleString">This is styled div</div>
     <h3>Kết hợp giữa class binding và style binding</h3>
     <div :class="['card', state.status ? 'active-card':'inactive-card']"
     :style="{backgroundColor:state.status ? 'lightgreen':'lightcoral'}">
     {{ state.name }} - {{ state.status }}
     </div>
     <hr>
     <h3>PROPERTY BINDING</h3>
     <p>Sử dụng fill giá trị vào các property của thẻ html</p>
     <input type="text" class="form-control" v-bind:value="cauNoiYeuThich">
     <h6>property src</h6>
     <img :src="logoUrl" alt="" style="height: 100px;"></img>
</template>

<!-- Viết code css cho vue hiện tại -->
<style scoped>
.active{
    background-color: green;
    color: white;
    padding: 10px;
}
.deactive{
    background-color: red;
    color: white;
    padding: 10px;
}
</style>
