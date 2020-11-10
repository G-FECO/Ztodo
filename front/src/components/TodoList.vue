<template>
<div class="square" align="center">
  <img class="startline" :src="lineUrl">
  <img class="startchar" :src="startUrl">
  <img class="finishflag" :src="flagUrl">
  <img class="finishchar" :src="finishUrl">
  <div class="divideline1"></div>
  <div class="divideline2"></div>
  <div class="divideline3"></div>
  <div class="row inner">
    <div class="partition">
      <h3>할 일</h3>
      <draggable class="list-group" :list="list1" group="people">
        <div
          class="list-group-item listitem"
          v-for="(element, index) in list1"
          :key="element.name"
        >
          {{ element.name }} {{ index }}
        </div>
      </draggable>
    </div>
    <div class="addbutton">
      <v-dialog
        v-model="dialog"
        persistent
        max-width="30%"
      >
          <template v-slot:activator="{on, attrs}">
            <v-btn
              class="mx-2"
              fab
              dark
              color="indigo"
              v-bind="attrs"
              v-on="on"
            >
              <v-icon dark>mdi-plus</v-icon>
            </v-btn>
          </template>
        <v-card>
          <v-card-title>
            <span class="headline">할 일 추가</span>
          </v-card-title>
          <v-card-text>
            <v-container>
              <v-row>
                <v-col>
                  <v-text-field
                    label="할 일이 뭔가요?"
                    v-model="todo"
                  >
                  </v-text-field>
                </v-col>
              </v-row>
            </v-container>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              color="blue darken-1"
              text
              @click="dialog=false"
            >
              닫기
            </v-btn>
            <v-btn
              color="blue darken-1"
              text
              @click="addTodo()"
            >
              추가
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>
    <div class="partition">
      <h3>진행 중</h3>
      <draggable class="list-group" :list="list2" group="people">
        <div
          class="list-group-item listitem"
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
          class="list-group-item listitem"
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
          class="list-group-item listitem"
          v-for="(element, index) in list4"
          :key="element.name"
        >
          {{ element.name }} {{ index }}
        </div>
      </draggable>
    </div>
  </div>
  <div class="outline1"></div>
  <div class="outline2"></div>
  <div class="outline3"></div>
  <div class="outline4"></div>
  <div class="diagonal1"></div>
  <div class="diagonal2"></div>
  <div class="dotDiagonal"></div>
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
      ],
      lineUrl: "https://upload.wikimedia.org/wikipedia/commons/thumb/a/ad/Race-bar.png/800px-Race-bar.png",
      startUrl: "https://upload.wikimedia.org/wikipedia/en/8/80/Start_%28%D0%BA%D0%B8%D0%BD%D0%BE%D1%82%D0%B5%D0%B0%D1%82%D1%80%29.png",
      flagUrl: "https://img.pngio.com/checkered-flag-finish-line-grand-free-vector-graphic-on-pixabay-race-car-starting-line-png-811_720.png",
      finishUrl: "https://finishlinecw.com/wp-content/uploads/2017/07/Logo-FinishLine_Carwash.png",
      dialog: false,
      todo: "",
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
    addTodo: function() {
      this.list1.push({ name: this.todo });
      this.dialog=false;
      this.todo="";
    }
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
  justify-content:center;
  align-content:center;
  display:grid;
  overflow: auto;
  background-color:grey;
  border-color: black;
}

.outline1 {
  position: absolute;
  width: 105px;
  height: 3px;
  top: 5%;
  left: 45%;
  background-color: black;
  transform: rotate();
}

.outline2 {
  position: absolute;
  width: 105px;
  height: 3px;
  top: 44.7%;
  left: 45%;
  background-color: black;
  transform: rotate();
}

.outline3 {
  position: absolute;
  width: 105px;
  height: 3px;
  top: 55%;
  left: 45%;
  background-color: black;
  transform: rotate();
}

.outline4 {
  position: absolute;
  width: 105px;
  height: 3px;
  top: 94.7%;
  left: 45%;
  background-color: black;
  transform: rotate();
}

.diagonal1 {
  position: absolute;
  width: 520px;
  height: 3px;
  top: 49.8%;
  left: 4.6%;
  background-color: black;
  transform: rotate(-11.4deg);
}

.diagonal2 {
  position: absolute;
  width: 520px;
  height: 3px;
  top: 49.87%;
  left: 44.4%;
  background-color: black;
  transform: rotate(-11.4deg);
}

.startline {
  position: absolute;
  transform: rotate(90deg);
  width: 35%;
  top: 23%;
  left: -16%;
}

.startchar {
  position: absolute;
  transform: rotate(90deg);
  width: 18%;
  top: 21%;
  left: -15%;
}

.finishflag {
  -moz-transform: scaleX(-1); 
  -o-transform: scaleX(-1); 
  -webkit-transform: scaleX(-1); 
  transform: scaleX(-1);
  position: absolute;
  width: 13%;
  top: 70%;
  left: 105%;
}

.finishchar {
  position: absolute;
  width: 30%;
  top: 73%;
  left: 85%;
  transform: rotate(90deg);
}

.divideline1 {
  position: absolute;
  width: 400px;
  height: 3px;
  top: 24.7%;
  left: 30.5%;
  border-style: dashed;
  border-color: whitesmoke;
  transform: rotate(90deg);
}

.divideline2 {
  position: absolute;
  width: 400px;
  height: 3px;
  top: 74.7%;
  left: 30.5%;
  border-style: dashed;
  border-color: whitesmoke;
  transform: rotate(90deg);
}

.divideline3 {
  position: absolute;
  width: 520px;
  height: 3px;
  top: 50%;
  left: 20%;
  border-style: dashed;
  border-color: whitesmoke;
  transform: rotate(-11.4deg);
}

.listitem {
  color:whitesmoke;
  cursor: pointer;
}

.addbutton {
  position: absolute;
  top: 12%;
  left: 5%;
}
</style>