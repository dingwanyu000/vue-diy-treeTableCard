<!--
  * @view
  * @author dingwy
  * @desc card信息组件
-->
<template>
  <div>
    <el-row>
      <el-col :span="6" v-for="subItem in item" :key="subItem.id" v-if="subItem.span == 24">
        <div style="height:20px"></div>
      </el-col>
      <el-col
        v-for="(subItem,index) in item"
        :key="subItem.name"
        :span="subItem.span == 24?18:subItem.span"
      >
        <div
          v-if="!noLine&&item.length == 1"
          style="border-left:3px solid #409EFF;height:20px;margin:0px 0px 0px 239px"
        ></div>
        <div
          v-else-if="!noLine&&item.length == 2&&index == 0"
          style="border-left:3px solid #409EFF;border-top:3px solid #409EFF;width:290px;height:20px;margin:0px 0px 0px 239px"
        ></div>
        <div
          v-else-if="!noLine&&item.length == 2&&index == 1"
          style="border-right:3px solid #409EFF;border-top:3px solid #409EFF;width:290px;height:20px;margin:0px 0px 0px -51px"
        ></div>
        <el-card style="border-radius: 5px 5px 5px 5px;width:480px">
          <div>
            <i
              v-if="subItem.expend"
              :id="subItem.id"
              @click="iClick"
              class="el-icon-minus"
              style="width:12px;height:12px;color:white;border-radius:50%;background-color:#EBEEF5;cursor:pointer"
            ></i>
            <el-table :data="subItem.array" style="width: 100%">
              <el-table-column :label="subItem.name">
                <el-table-column label="输入">
                  <el-table-column prop="fileNum" label="文件数" min-width="20%"></el-table-column>
                  <el-table-column prop="recordNum" label="记录数" min-width="20%"></el-table-column>
                </el-table-column>
                <el-table-column label="输出">
                  <el-table-column prop="goTo" label="去向" min-width="20%"></el-table-column>
                  <el-table-column prop="outFileNum" label="文件数" min-width="20%"></el-table-column>
                  <el-table-column prop="outRecordNum" label="记录数" min-width="20%"></el-table-column>
                </el-table-column>
              </el-table-column>
            </el-table>
          </div>
        </el-card>
        <div
          v-if="subItem.children.length != 0"
          style="border-left:3px solid #409EFF;height:20px;margin:0px 0px 0px 239px"
        ></div>
      </el-col>
    </el-row>
    <div v-if="item.length > 0">
      <info-card
        v-for="nodeItem in item"
        :key="nodeItem.name"
        :item="nodeItem.children"
        :noLine="false"
        :data="data"
      ></info-card>
    </div>
  </div>
</template>
<script>
export default {
  name: "infoCard",
  props: {
    item: {
      type: Array
    },
    data: {
      type: Array
    },
    noLine: {
      type: Boolean
    }
  },
  mounted() {
    this.copyData = JSON.parse(JSON.stringify(this.$props.data));
  },
  methods: {
    iClick(e) {
      if (e.currentTarget.className == "el-icon-plus") {
        bus.$emit("child-plus");
        e.currentTarget.className = "el-icon-minus";
      } else {
        this.traverse(e, this.copyData);
        bus.$emit("child-minus", this.copyData);
        e.currentTarget.className = "el-icon-plus";
      }
    },
    traverse(e, array) {
      for (let i = 0; i < array.length; i++) {
        if (e.currentTarget.id == array[i].id) {
          array[i].children = [];
          array = array.slice(0, i + 1);
          break;
        } else if (array[i].children.length > 0) {
          this.traverse(e, array[i].children);
        }
      }
      this.copyData = array;
    }
  }
};
</script>
