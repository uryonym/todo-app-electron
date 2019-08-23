<template>
  <el-main>
    <el-input @keypress.enter.native="insertTask" v-model="input" placeholder="タスク名を入力">
      <el-button slot="append" size="mini" @click="insertTask">追加</el-button>
    </el-input>
    <el-table :data="taskList" :show-header="false" stripe>
      <el-table-column prop="task" width="auto"></el-table-column>
      <el-table-column align="center" width="100%">
        <template slot-scope="record">
          <el-button size="mini" type="danger" @click="deleteTask(record.$index)">削除</el-button>
        </template>
      </el-table-column>
    </el-table>
  </el-main>
</template>

<script>
  export default {
    name: 'TodoList',
    data () {
      return {
        taskList: [],
        input: ''
      }
    },
    methods: {
      insertTask () {
        if (this.input === '') { return }
        this.taskList.push({task: this.input})
        this.input = ''
      },
      deleteTask (index) {
        this.taskList.splice(index, 1)
      }
    }
  }
</script>

<style scoped>
  main {
    width: 600px;
    margin: 0 auto;
  }
</style>
