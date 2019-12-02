<template>
  <div>
    <div style="display: flex;justify-content: flex-start">
      <!--  -->
      <el-input placeholder="111111"
                prefix-icon="el-icon-search"
                v-model="keywords">
      </el-input>
      <!--  -->
      <el-button type="primary"
                 icon="el-icon-search"
                 @click="searchClick">搜索</el-button>
      <!--  -->
      <el-table ref="multipleTable"
                :data="articles"
                tooltip-effect="dark"
                style="width: 100%;overflow-x: hidden; overflow-y: hidden;"
                max-height="390"
                @selection-change="handleSelectionChange"
                v-loading="loading">
        <el-table-column type="selection"
                         width="35"
                         align="left"
                         v-if="showEdit || showDelete">
        </el-table-column>
        <el-table-column label="姓名"
                         width="400"
                         align="left">
          <template slot-scope="scope"><span style="color: #409eff;cursor: pointer"
                  @click="itemClick(scope.row)">{{ scope.row.title}}</span>
          </template>
        </el-table-column>

        <el-table-column label="操作"
                         align="left"
                         v-if="showEdit || showDelete">
          <template slot-scope="scope">
            <el-button size="mini"
                       @click="handleEdit(scope.$index, scope.row)"
                       v-if="showEdit">编辑
            </el-button>
            <el-button size="mini"
                       type="danger"
                       @click="handleDelete(scope.$index, scope.row)"
                       v-if="showDelete">删除
            </el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
  </div>
</template>

<script>
import { getRequest } from '../utils/api'
import { putRequest } from '../utils/api'

export default {
  data () {
    return {
      // 搜索框
      keywords: '',
    }
  }
}
</script>

<style scoped>
</style>