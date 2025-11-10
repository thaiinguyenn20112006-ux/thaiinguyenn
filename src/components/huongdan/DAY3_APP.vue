<!-- code js -->
 <script setup>
 import{ref, reactive} from 'vue';
 let age= ref(18);
 let scoped =ref(80);
 let isAbsent = ref(true);
 const toggleAbsent=()=>{
    isAbsent.value=!isAbsent.value;
 }
// Mảng đối tượng
let list_foods =reactive([
    {id: 'F01', name:"Bún bò huế", quantity: 10, price: 50000},
    {id: 'F02', name:"Cơm rang dưa bò", quantity: 15, price: 35000},
    {id: 'F03', name:"Lẩu ếch", quantity: 11, price: 250000},
    {id: 'F04', name:"Bạc xỉu", quantity: 10, price: 50000},
])
const totalCartValue=()=>{
    return list_foods.reduce((total,item)=>{
        return total+ item.price*item.quantity;
    },0)
    // let total =0;
    // for(item in list_foods){
    //     total+= item.price*item.quantity;
    // }
}
</script>
 <!-- html -->
  <template>
    <div class="container">
        <h3>V-IF/ V-ELSE</h3>
        <div v-if="age>=18" class="alert alert-success mt-4">Bạn đã đủ tuổi</div>
        <div v-else class="alert alert-danger mt-4">Bạn chưa đủ tuổi</div>
        <p>Thông báo xếp hangk</p>
        <span v-if="scoped>=90">Xuất sắc</span>
        <span v-else-if="scoped>=80">Giỏi</span>
        <span v-else-if="scoped>=60">Khá</span>
        <span v-else-if="scoped>=20">Trung bình</span>
        <span v-else>Yếu</span>
        <h3>v-show: check điểm danh</h3>
    <div v-show="!isAbsent" class="alert alert-success">Có mặt</div>
    <div v-show="isAbsent" class="alert alert-danger">Vắng mặt</div>
    <button
      @click="toggleAbsent"
      :class="isAbsent ? 'btn btn-danger' : 'btn btn-primary'"
    >
      {{ isAbsent ? "Vắng mặt" : "Có mặt" }}
    </button>
    <h3> list redering</h3>
    <p>Danh sách món ăn</p>
    <ul v-for="a in list_foods":key="item">
        <li>{{ a }}</li>
    </ul>
    <p>Danh sách món ăn kèm món, kèm theo index</p>
    <ul v-for="(item,index) in list_foods":key="index">
        <li>{{ index }} - {{ item.price*item.quantity }}</li>
    </ul>
    <!-- giỏ hàng -->
     <table class="table">
        <thead>
            <tr>
                <td>ID</td>
                <td>Tên</td>
                <td>Số lượng</td>
                <td>Giá</td>
                <td>Tổng tiền...</td>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(food,index) in list_foods":key="food.id">
                <td>{{ food.id }}</td>
                <td>{{ food.name }}</td>
                <td>{{ food.quantity }}</td>
                <td>{{ food.price }}</td>
                <td>{{ (food.price*food.quantity).toFixed(2) }}</td>
            </tr>
        </tbody>
     </table>
     <h2>Tổng tiền giỏ hàng:{{ totalCartValue() }}</h2>
    </div>
   
  </template>
  <!-- code css -->
   <style scoped></style>