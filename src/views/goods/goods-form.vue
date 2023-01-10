<template>
    <div>
        <div class="good-form">
            <el-page-header @back="$router.back()" :content="`商品${id?'编辑':'添加'}`"></el-page-header>
            <el-form style="width: 600px; margin-top: 20px" :model="ruleForm" :rules="rules" ref="ruleForm"
                label-width="100px" class="demo-ruleForm">
                <!-- 商品名称 -->
                <!-- prop="name" 前端进行数据校验 -->
                <el-form-item label="商品名称" prop="name">
                    <el-input></el-input>
                </el-form-item>

                <!-- 商品描述 -->
                <el-form-item label="商品描述" prop="desc">
                    <el-input type="texterea" rows="3"></el-input>
                </el-form-item>

                <!-- 商品分类 -->
                <el-form-item label="商品分类" prop="cate">

                </el-form-item>

                <!-- 商品价格 -->
                <el-form-item label="商品价格">
                    <el-input-number :min="0" :step="0.1" :precision="2"></el-input-number>
                </el-form-item>

                <!-- 是否热销 -->
                <el-form-item label="是否热销">
                    <el-switch></el-switch>
                </el-form-item>

                <!-- 商品图片 -->
                <el-form-item label="商品图片" prop="type">

                </el-form-item>

                <el-form-item>
                    <el-button type="primary">提交</el-button>
                    <el-button>重置</el-button>
                </el-form-item>
            </el-form>
        </div>
    </div>
</template>
<script>
export default {
    name: '',
    props: [],
    data() {
        return {

        }
    },
    methods: {

    },
}
</script>
<style lang="scss" scoped>
.good-form {
    box-sizing: border-box;
    padding: 20px;
}
</style>