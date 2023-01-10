<template>
    <div>
        <el-row>
            <el-col :span="24">
                <el-input v-model="input" placeholder="请输入内容" v-model.trim="name" style="width:135px"></el-input>
                <cateselect v-model="cate" clearable></cateselect>
                <el-date-picker type="daterange" range-separator="至" start-placeholder="开始日期"
                    end-placeholder="结束日期"></el-date-picker>
                <el-button type="primary" icon="el-icon-search" @click="searchclick">搜索</el-button>
                <el-button type="primary" icon="el-icon-edit" @click="$router.push('/good/add')">添加</el-button>
                <el-button type="primary" icon="el-icon-download">导出</el-button>
                <el-checkbox style="margin-left:20px">审核人</el-checkbox>
                <!-- 表格 -->
                <el-table :data="list" border style="width: 100%; margin-top: 20px">
                    <el-table-column prop="id" label="序号" align="center" sortable width="180">
                        <template slot-scope="{ row, $index }">
                            <div>{{ $index + 1 }}</div>
                        </template>
                    </el-table-column>
                    <el-table-column prop="name" label="商品" align="center" width="180">
                        <template slot-scope="{ row,}">
                            <img :src="`http://47.94.210.129:9999${row.img}`" style="width: 60px" alt />
                            <div>{{ row.name }}</div>
                        </template>
                    </el-table-column>

                    <el-table-column prop="price" label="价格" align="center">
                        <template slot-scope="{ row,  }">
                            <div>{{ `￥${row.price.toFixed(2)}` }}</div>
                        </template>
                    </el-table-column>

                    <el-table-column prop="cate" label="品类" align="center">
                        <template slot-scope="{ row,  }">
                            <div>{{ cateZH(row.cate) }}</div>
                        </template>
                    </el-table-column>

                    <el-table-column prop="hot" label="是否热销" align="center">
                        <template slot-scope="{ row,  }">
                            <div>{{ row.hot ? "是" : "否" }}</div>
                        </template>
                    </el-table-column>

                    <el-table-column prop="create_time" label="发布时间" align="center">
                        <template slot-scope="{ row,  }">
                            <div>{{ row.create_time | time }}</div>
                        </template>
                    </el-table-column>

                    <el-table-column prop="check_status" label="商品状态" align="center">
                        <template slot-scope="{ row,  }">
                            <div>{{ row.check_status ? "已上架" : "待审核" }}</div>
                        </template>
                    </el-table-column>

                    <el-table-column label="操作" width="230" align="center">
                        <template slot-scope="{ row }">
                            <el-button type="primary" size="mini" @click="toedit(row)">编辑</el-button>
                            <el-button v-if="row.published" type="primary" size="mini">详情</el-button>
                            <el-button v-else type="success" size="mini" v-permission="['admin']">审核</el-button>
                            <el-button size="mini" type="danger" @click="delgood(row)">删除</el-button>
                        </template>
                    </el-table-column>
                </el-table>
                <!-- 分页 -->
                <el-pagination style="margin-top: 20px" @size-change="handleSizeChange"
                    @current-change="handleCurrentChange" :current-page="page" :page-sizes="[3, 5, 10, 20]"
                    :page-size="size" layout="total, sizes, prev, pager, next, jumper" :total="total"></el-pagination>
            </el-col>
        </el-row>
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
.el-row {
    margin-bottom: 20px;

    &:last-child {
        margin-bottom: 0;
    }
}

.el-col {
    border-radius: 4px;
}

.bg-purple-dark {
    background: #99a9bf;
}

.bg-purple {
    background: #d3dce6;
}

.bg-purple-light {
    background: #e5e9f2;
}

.grid-content {
    border-radius: 4px;
    min-height: 36px;
}

.row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
}
</style>