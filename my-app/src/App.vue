<template>
  <div id="app">
    <img src="./assets/logo.png" height="32" width="32">
    <h4>{{ msg }}</h4>

    <div v-for="(list, listName) in layout.tags" class="v-col--auto" :key="listName">
      <div class="panel">
          <div class="panel__heading">
            <h3 style="color: palevioletred">Tags {{listName}}</h3>
          </div>
          <div class="panel__body">
            <vddl-list class="panel__body--list" :list="list" :allowed-types="['rows','cols']" :horizontal="false">
                <vddl-draggable class="panel__body--item" v-for="(item, index) in list" :key="item.id"
                  :draggable="item"
                  :tag="'label'"
                  :index="index"
                  :wrapper="list"
                  :type="listName"                  
                  effect-allowed="move">
                  <vddl-nodrag class="nodrag" style="display: inline">
                    <input type="checkbox" v-model="item.show" />
                  {{item.title}}
                  </vddl-nodrag>
                  <vddl-handle
                    :handle-left="20"
                    :handle-top="20"
                    class="handle-metrics"
                    style="display: inline">
                    <i class="fa fa-arrows"></i>                    
                  </vddl-handle>
                </vddl-draggable>
                <vddl-placeholder class="tags">Drop any <strong>tag</strong> here</vddl-placeholder>
            </vddl-list>
          </div>
      </div>
    </div>

    <div class="panel">
          <div class="panel__heading">
            <h3 style="color: peru">Metrics</h3>
          </div>
          <div class="panel__body">
            <vddl-list class="panel__body--list" :list="layout.metrics" :allowed-types="['metrics']" :horizontal="false">
                <vddl-draggable class="panel__body--item" v-for="(item, index) in layout.metrics" :key="item.id"
                  :draggable="item"
                  :tag="'label'"
                  :index="index"
                  :wrapper="layout.metrics"
                  :type="'metrics'"   
                  effect-allowed="move">
                  <vddl-nodrag class="nodrag" style="display: inline">
                    <input type="checkbox" v-model="item.show"/>
                  {{item.title}}
                  </vddl-nodrag>
                  <vddl-handle
                    :handle-left="20"
                    :handle-top="20"
                    class="handle-metrics"
                    style="display: inline">
                    <i class="fa fa-arrows"></i>                    
                  </vddl-handle>
                </vddl-draggable>
                <vddl-placeholder class="metrics">Drop any <strong>metric</strong> here</vddl-placeholder>
            </vddl-list>
          </div>
    </div>

    <div>
      <p style="color: palevioletred">Tags on rows: {{layout.tags.rows}}</p>
    </div>
    <div>
      <p style="color: palevioletred">Tags on cols: {{layout.tags.cols}}</p>
    </div>
    <div>
      <p style="color: peru">Metrics: {{layout.metrics}}</p>
    </div>

  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      msg: "Welcome to vddl Demo",
      layout: {
        tags: {
          rows: [
            {
              id: 1,
              title: "tag1",
              name: "tag1name",
              show: true
            },
            {
              id: 2,
              title: "tag2",
              name: "tag2name",
              show: true
            },
            {
              id: 3,
              title: "tag3",
              name: "tag3name",
              show: false
            },
            {
              id: 4,
              title: "tag4",
              name: "tag3name",
              show: false
            }
          ],
          cols: []
        },
        metrics: [
          {
            id: 1,
            title: "metric1",
            show: true
          },
          {
            id: 2,
            title: "metric2",
            show: true
          },
          {
            id: 3,
            title: "metric3",
            show: true
          },
          {
            id: 4,
            title: "metric4",
            show: true
          },
          {
            id: 5,
            title: "metric5",
            show: true
          },
          {
            id: 6,
            title: "metric6",
            show: true
          }
        ]
      }
    };
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.vddl-list,
.vddl-draggable {
  position: relative;
}

.vddl-list {
  min-height: 44px;
}

.vddl-dragging {
  opacity: 0.7;
}

.vddl-dragging-source {
  display: none;
}

.vddl-placeholder.tags {
  color: palevioletred;
}

.vddl-placeholder.metrics {
  color: peru;
}

/* .handle-metrics {
  cursor: move;
  width: 20px;
  height: 20px;
  background: url("./assets/logo.png") center center no-repeat;
  background-size: 20px 20px;
}

.nodrag {
  flex: 1;
  display: flex;
} */


</style>
