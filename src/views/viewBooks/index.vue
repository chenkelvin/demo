<!--
 * @Author: kelvin
 * @Date: 2019-12-17 21:58:19
 * @LastEditTime: 2021-04-06 22:40:05
 * @FilePath: /viewBooks/src/views/viewBooks/index.vue
 * @Description: 内页
-->

<template>
    <div class="app-index-layout">
        <el-form ref="form" :model="searchForm">
            <el-row :gutter="10">
                <el-col :span="6">
                    <el-form-item label=" ">
                        <el-input
                            v-model="searchForm.bookName"
                            placeholder="书名"
                        ></el-input>
                    </el-form-item>
                </el-col>
                <el-col :span="2">
                    <el-form-item class="fl">
                        <el-button type="primary" @click="jumpPiano"
                            >搜索</el-button
                        >
                    </el-form-item>
                </el-col>
            </el-row>
        </el-form>
        <el-row>
            <!-- 内容 -->
            <el-col>
                <div class="books-main-layout">
                    <el-row></el-row>
                    <h3>书籍</h3>
                    <!-- border 边框 -->
                    <!-- stripe 带斑马纹 -->
                    <el-table
                        :data="tableData"
                        stripe
                        border
                        style="width: 100%"
                    >
                        <el-table-column
                            prop="name"
                            label="书名"
                            width="200"
                            show-overflow-tooltip
                        ></el-table-column>
                        <el-table-column
                            prop="page"
                            label="页数"
                            width="60"
                        ></el-table-column>
                        <el-table-column prop="desc" label="描述">
                            <template scope.row="cope.row.desc">
                                <div @click="jumpToDtl">第一章 灭门</div>
                            </template>
                        </el-table-column>
                    </el-table>
                </div>
                <!-- 分页 -->
                <div class="block">
                    <el-row>
                        <el-col align="right">
                            <el-pagination
                                :current-page="currentPage"
                                :total="pageTotal"
                                :page-size="pageSize"
                                :page-sizes="pageSizes"
                                @current-change="handleCurrentChange"
                                @size-change="handleSizeChange"
                                layout="total, sizes, prev, pager, next, jumper"
                                background
                            ></el-pagination>
                        </el-col>
                    </el-row>
                </div>
            </el-col>
        </el-row>
    </div>
</template>

<script>
export default {
    data() {
        return {
            tableData: [
                {
                    id: 2,
                    name: "笑傲江湖",
                    page: 300,
                    desc: "令狐冲",
                },
            ],
            currentPage: 1, // page start
            pageTotal: 100,
            pageSize: 10,
            pageSizes: [10, 20, 50, 100],
            searchForm: {
                // 搜索条件
                bookName: "",
            },
        };
    },
    created() {
        this.initPage();
    },
    methods: {
        /**
         * 页面初始化
         */
        initPage() {
            console.error("init");
        },
        handleOpen(key, keyPath) {
            console.log(key, keyPath);
        },
        handleClose(key, keyPath) {
            console.log(key, keyPath);
        },
        handleSizeChange() {
            this.$message.warning("分页大小改变");
        },
        handleCurrentChange() {
            this.$message.warning("改变当前页");
        },
        /**
         * 钢琴页面
         */
        jumpPiano() {
            this.$router.push({
                path: "/piano",
            });
        },
        /**
         * @desc 跳转书籍详情页
         * GitHub链接太难，经常链接不到，想换掉了。。。
         */
        jumpToDtl() {
            this.$router.push({
                path: "/booksDtl",
            });
        },
    },
};
</script>

<style lang="scss">
.books-main-layout {
    padding: 10px 0;
}
</style>
