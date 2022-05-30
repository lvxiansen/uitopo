<template>
  <div id="container"></div>
</template>

<script>
import { Graph } from '@antv/x6';

export default {
  name: "uitest",
  data: () => ({
    data: {
      nodes: [],
      edges: [],
      graph: null,
    },
  }),
  mounted() {
    this.getData();
    this.initGraph();
  },
  methods:{
    initGraph() {
      const graph = new Graph({
        container: document.getElementById('container'),
        width: 800,
        height: 600,
        background:{
          color: '#fffbe6', // 设置画布背景颜色
        },
        grid: {
          size: 10,      // 网格大小 10px
          visible: true, // 渲染网格背景
        }
      })
      graph.fromJSON(this.data)
      // graph.zoom(-0.5)
      // graph.translate(100,20)
    },
    getData() {
      this.data.nodes = [
        {
          id: 'node1', // String，可选，节点的唯一标识
          x: 40,       // Number，必选，节点位置的 x 值
          y: 40,       // Number，必选，节点位置的 y 值
          width: 80,   // Number，可选，节点大小的 width 值
          height: 40,  // Number，可选，节点大小的 height 值
          label: 'hello', // String，节点标签
          shape:'rect',
        },
        {
          id: 'node2', // String，节点的唯一标识
          x: 160,      // Number，必选，节点位置的 x 值
          y: 180,      // Number，必选，节点位置的 y 值
          width: 80,   // Number，可选，节点大小的 width 值
          height: 40,  // Number，可选，节点大小的 height 值
          label: 'world', // String，节点标签
          shape:'ellipse',
        },
      ];
      this.data.edges = [
        {
          source: 'node1', // String，必须，起始节点 id
          target: 'node2', // String，必须，目标节点 id
          attrs: {
            line: {
              stroke:'black',
            },
          },
        },
      ];
    },
  },

}
</script>

<style scoped>

</style>