<!-- Cấu hình -->
<script setup>
//  khai báo các biến dạng chuỗi
let courseName = "Framework Vue 3";
let courseLevel = 'Nâng cao';
// Khái báo biến dạng số
let courseTime = 30;
// khái báo biến dạng boolean
let courseIsActive = true;
</script>
<!-- viết code html -->
<template>
    <div class="container">
        <h1 class="display-4 mb-3">
            Thông tin:
        </h1>
        <ul class="list-group">
            <li class="list-grop-item">
                Tên khoá học:{{ courseName }}
            </li>
            <li class="list-grop-item">
                Cấp độ:{{ courseLevel }}
            </li>
            <li class="list-grop-item">
                Thời gian:{{ courseTime }} giờ
            </li>
            <li class="list-grop-item">
                Trạng thái:{{ courseIsActive ? 'Đang mở' : 'Đã đóng' }}
            </li>
            <li></li>
            <li></li>
        </ul>
    </div>
</template>

<!-- Viết code css cho vue hiện tại -->
<style scoped></style>