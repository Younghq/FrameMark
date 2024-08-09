<template>
    <div class="main-background">
        <!-- 图片相框区域 -->
        <div class="img-frame" :style="img_style">
            <div class="img">
                <!-- 图像处理插件 -->
                <img src="../assets/img/20240803-P1022355.jpg" alt="">
                <div class="img-info">
                    <p>{{ img_camera }}</p>
                    <p>{{ img_camera_lens }}</p>
                    <p>{{ img_camera_drop_shutter }}</p>
                </div>
            </div>
        </div>
        <!-- 图片编辑区域 -->
        <div class="img-edit-container">
            <!-- 文本编辑区 -->
            <div class="img-info-edit">
                <p>相机：</p>
                <input type="text" v-model="img_camera">
                <p>镜头：</p>
                <input type="text" v-model="img_camera_lens">
                <p>快门：</p>
                <input type="text" v-model="img_camera_drop_shutter">
                <p>边框厚度：</p>
                <input type="range" min="0" max="100" value="50" class="slider" id="mySlider"
                    v-model.number="img_camera_padding">
                <p>边框圆角：</p>
                <input type="range" min="0" max="100" value="50" class="slider" id="mySlider"
                    v-model.number="img_camera_br">
            </div>
            <!-- 保存 -->
            <div class="edit-btn-group">
                <TheButton>复位</TheButton>
                <TheButton>保存</TheButton>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import TheButton from "./TheButton.vue";

const img_camera = ref("Shot by Lumix S5");  // 相机
const img_camera_lens = ref("50mm F1.8"); // 镜头
const img_camera_drop_shutter = ref("400/1"); // 快门
const img_camera_padding = ref(12); // 边框厚度
const img_camera_br = ref(12); // 边框圆角

const img_style = computed(() => ({
    padding: img_camera_padding.value + 'px',
    borderRadius: img_camera_br.value + 'px',
}));
</script>




<style scoped>
.main-background {
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #B3495C;
    height: 100vh;
    /* 确保全屏高度 */
    width: 100vw;
    flex-direction: column;
}

.img-frame {
    display: flex;
    /* 设置主轴为垂直方向 */
    flex-direction: column;
    /* 垂直方向从顶部开始 */
    justify-content: flex-start;
    /* 水平方向居中 */
    align-items: center;
    width: 400px;
    background-color: white;

    /* 可变的边框内边距 - 动态css */
    /* padding: 1rem; */
    /* 可变的边框圆角 - 动态css */
    /* border-radius: 2px; */
}

.img-frame img {
    max-width: 100%;
    max-height: 400px;
}


.img-info {
    display: flex;
    flex-direction: column;
    /*自底向上*/
    justify-content: flex-end;
}

.img-info p {
    padding: 0px;
    margin: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.img-edit-container {
    margin-top: 3rem;
    background-color: white;
    padding: 1.5rem 0.8rem 1rem 0.8rem;
    width: 300px;
    border-radius: 1rem;
}

.img-info-edit {
    display: grid;
    grid-template-columns: auto auto;

    justify-content: center;
    align-items: center;
    grid-gap: 0px;
    /* 网格项之间的间距 */
}

.img-info-edit>p {
    margin: 8px 0px 8px 0px;
}


.edit-btn-group {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}

.edit-btn-group button {
    margin: 0px 0.5rem 0px 0.5rem;
}
</style>