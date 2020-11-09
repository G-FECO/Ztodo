<template>
<div class="square" align="center">
  <div class="row inner">
    <div class="partition">
      <h3>할 일</h3>
      <draggable class="list-group" :list="list1" group="people">
        <div
          class="list-group-item"
          v-for="(element, index) in list1"
          :key="element.name"
        >
          {{ element.name }} {{ index }}
        </div>
      </draggable>
    </div>
    <div class="partition">
      <h3>진행 중</h3>
      <draggable class="list-group" :list="list2" group="people">
        <div
          class="list-group-item"
          v-for="(element, index) in list2"
          :key="element.name"
        >
          {{ element.name }} {{ index }}
        </div>
      </draggable>
    </div>
  </div>
  <div class="row inner">
    <div class="partition">
      <h3>테스트</h3>
      <draggable class="list-group" :list="list3" group="people">
        <div
          class="list-group-item"
          v-for="(element, index) in list3"
          :key="element.name"
        >
          {{ element.name }} {{ index }}
        </div>
      </draggable>
    </div>
    <div class="partition">
      <h3>완료</h3>
      <draggable class="list-group" :list="list4" group="people">
        <div
          class="list-group-item"
          v-for="(element, index) in list4"
          :key="element.name"
        >
          {{ element.name }} {{ index }}
        </div>
      </draggable>
    </div>
  </div>
</div>
</template>
<script>
import draggable from "vuedraggable";
export default {
  name: "TodoList",
  order: 1,
  components: {
    draggable
  },
  data() {
    return {
      list1: [
        { name: "John", id: 1 },
        { name: "Joao", id: 2 },
        { name: "Jean", id: 3 },
        { name: "Gerard", id: 4 },
      ],
      list2: [
        { name: "Juan", id: 5 },
        { name: "Edgard", id: 6 },
        { name: "Johnson", id: 7 }
      ],
      list3: [
        { name: "aaa", id: 8 },
        { name: "bbb", id: 9 },
        { name: "ccc", id: 10 },
      ],
      list4: [
        { name: "ddd", id: 11 },
        { name: "eee", id: 12}
      ]
    };
  },
  methods: {
    add: function() {
      this.list.push({ name: "Juan" });
    },
    replace: function() {
      this.list = [{ name: "Edgard" }];
    },
    clone: function(el) {
      return {
        name: el.name + " cloned"
      };
    },
  }
};
</script>
<style>
.square {
  width: 1024px;
  height: 1024px;
  position: relative;
  margin: 3% auto;
}

.square:after {
  content: "";
  display: block;
  padding-bottom: 100%;
}

.inner {
  position: relative;
  height: 50%;
  width: 100%;
}

.partition {
  position: relative;
  width: 40%;
  height: 80%;
  margin: 5%; 
  border-style: solid;
  border-radius: 100px;
}
</style>