<template>
  <div id="app">
    <img src="./assets/logo.png" height="32" width="32">
    <h4>{{ msg }}</h4>

    <div v-for="(list, listName) in layout.dimensions" class="v-col--auto" :key="listName">
      <div class="panel">
          <div class="panel__heading">
            <h3>Dimensions {{listName}}</h3>
          </div>
          <div class="panel__body">
            <vddl-list class="panel__body--list" :list="list" :horizontal="false">
                <vddl-draggable class="panel__body--item" v-for="(item, index) in list" :key="item.id"
                  :draggable="item"
                  :index="index"
                  :wrapper="list"
                  effect-allowed="move">
                  {{item.title}}
                </vddl-draggable>
                <vddl-placeholder class="red">Drag it here</vddl-placeholder>
            </vddl-list>
          </div>
      </div>
    </div>

    <div class="panel">
          <div class="panel__heading">
            <h3>Metrics</h3>
          </div>
          <div class="panel__body">
            <vddl-list class="panel__body--list" :list="layout.metrics" :horizontal="false">
                <vddl-draggable class="panel__body--item" v-for="(item, index) in layout.metrics" :key="item.id"
                  :draggable="item"
                  :index="index"
                  :wrapper="layout.metrics"
                  effect-allowed="move">
                  {{item.title}}
                </vddl-draggable>
                <vddl-placeholder class="red">Drag it here</vddl-placeholder>
            </vddl-list>
          </div>
    </div>

    <div>
      <p>Dimension on rows: {{layout.dimensions.rows}}</p>
    </div>
    <div>
      <p>Dimension on cols: {{layout.dimensions.cols}}</p>
    </div>
    <div>
      <p>Metrics: {{layout.metrics}}</p>
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
        dimensions: {
          rows: [
            {
              id: 1,
              title: "tag1",
              name: "tag1name"
            },
            {
              id: 2,
              title: "tag2",
              name: "tag2name"
            },
            {
              id: 3,
              title: "tag3",
              name: "tag3name"
            },
            {
              id: 4,
              title: "tag4",
              name: "tag3name"
            }
          ],
          cols: []
        },
        metrics: [
          {
              id: 1,
              title: "metric1"
            },
            {
              id: 2,
              title: "metric2"
            },
            {
              id: 3,
              title: "metric3"
            },
            {
              id: 4,
              title: "metric4"
            },
            {
              id: 5,
              title: "metric5"
            },
            {
              id: 6,
              title: "metric6"
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
</style>
