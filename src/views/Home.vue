<template>
  <div class="home">
    <span
      ><strong
        >"@handsontable/vue": "^3.1.0","handsontable":
        "^6.2.2"版本为MIT开源协议</strong
      ></span
    >
    <br />
    <button @click="refresh">刷新</button>
    <br />
    <hot-table
      ref="hotTableComponent"
      class="table"
      :settings="settings"
    ></hot-table>
  </div>
</template>

<script>
import { HotTable } from "@handsontable/vue";
export default {
  name: "Home",
  data() {
    return {
      originData: [
        "红标",
        "单位客户法定名称",
        "Corporation CustomerLegal Name",
        "varchar2",
        1000,
        1000,
        "文本型",
        "IP100002",
        "测试",
        "ceshi",
        "昭通",
        "赵仝",
        "字段备注备注备注",
      ],
      settings: {
        language: "zh-CN",
        data: [
          [
            "红标",
            "单位客户法定名称",
            "Corporation CustomerLegal Name",
            "varchar2",
            1000,
            1000,
            "文本型",
            "IP100002",
            "测试",
            "ceshi",
            "昭通",
            "赵仝",
            "字段备注备注备注",
            "红标",
            "通过",
            "红标",
          ],
        ],
        // colHeaders: true,
        colHeaders: [
          "贯标结果",
          "中文字段名",
          "英文字段名",
          "字段类型",
          "字段长度",
          "字段精度",
          "标准类型",
          "数据标准编号",
          "表中文名称",
          "表英文名称",
          "维护系统",
          "维护人",
          "备注",
          "数据贯标",
          "贯标意见说明",
          "贯标结果",
          "数据贯标审核",
          "贯标审核意见",
        ],
        rowHeaders: true,
        contextMenu: [
          "row_above",
          "row_below",
          "col_left",
          "col_right",
          "remove_row",
          "remove_col",
          "---------",
          "undo",
          "redo",
          "commentsAddEdit",
          "commentsRemove",
        ],
        fixedColumnsLeft: 1,
        columns: [
          {
            editor: "select",
            selectOptions: ["红标", "黄标", "绿标", "无标准映射"],
          },
          {},
          {},
          {},
          {},
          {},
          {},
          {},
          {},
          {},
          {},
          {},
          {},
          {},
          {},
          {
            type: "dropdown",
            source: ["红标", "黄标", "绿标", "无标准映射"],
          },
        ],
        manualRowMove: true,
        manualColumnMove: true,
        manualColumnFreeze: true,
        comments: true
      },
    };
  },
  components: {
    HotTable,
  },
  mounted() {
    for (let i = 0; i < 50; i++) {
      this.settings.data.push(JSON.parse(JSON.stringify(this.originData)));
    }
    let hot = this.$refs.hotTableComponent.hotInstance;
    let plugin = hot.getPlugin("manualColumnFreeze");
    plugin.enablePlugin();
    console.log(plugin);
    //plugin.freezeColumn(5)
  },
  methods: {
    refresh() {
      this.$router.go(0);
    },
  },
};
</script>
<style src="../../node_modules/handsontable/dist/handsontable.full.css"></style>
<style lang="less" scoped>
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
  .table {
    width: 80%;
    height: 500px;
    overflow: hidden;
    border: 1px solid red;
  }
}
</style>
