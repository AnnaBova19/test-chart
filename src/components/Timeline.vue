<template>
  <div class="wrapper">
    <div class="wrapper-container flex-center">
      <div class="timeline-container flex-center">
        <div v-for="year in yearsArray" :key="year" class="timeline-block flex-center">
          <div v-for="scale in new Array(12)" :key="scale" class="scale-block"></div>
          <div class="year-block">{{year}}</div>
        </div>
      </div>
    </div>

    <!-- Left menu -->
    <div class="left-wrap flex-center">
      <div class="left-tabs flex-center">
        <div v-for="(item, index) in leftMenu" :key="item.title"
          class="tab-item" 
          :class="{'active-left': leftActiveTab === index}"
          @click="handleLeftClick(item, index)">
          <img 
            class="tab-icon"
            :src="require(`@/assets/icons/${item.icon}`)"/>
          {{ item.title }}
        </div>
      </div>
    </div>

    <!-- Right menu -->
    <div class="right-tabs flex-center">
      <div v-for="(item, index) in rightMenu" :key="item"
        class="tab-item" 
        :class="{'active-right': rightActiveTab === index}"
        @click="handleRightClick(item, index)">
        {{ item }}
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class HelloWorld extends Vue {
  private leftMenu = [
    { title: 'Timeline', icon: 'clock.svg' },
    { title: 'Whiteboard', icon: 'board.svg' },
  ]
  private rightMenu = ['All time', 'Last year', '6 months', '1 month', '2 weeks', '1 week', 'Custom']
  private leftActiveTab = 0
  private rightActiveTab = 0

  get yearsArray() {
    const arr = []
    for (let i = 2000; i <= 2021; i++) {
      arr.push(i)
    }
    return arr
  }

  handleLeftClick(item: any, index: number): void {
    this.leftActiveTab = index
    console.log(item.title)
  }

  handleRightClick(item: any, index: number): void {
    this.rightActiveTab = index
    console.log(item)
  }
}
</script>

<style scoped>
.flex-center {
  display: flex;
  align-items: center;
}
.wrapper {
  width: 100%;
  max-width: 1562px;
  height: 8vw;
  background-color: #ffffff;
  position: relative;
  border: .5px solid #d8d8d8;
}
.wrapper-container {
  width: calc(100% - 6px);
  height: calc(100% - 3px);
  margin: 3px 3px 0;
  background-color: #f8fafc;
}
.left-wrap {
  position: absolute;
  top: 0;
  left: 0;
}
.left-tabs {
  box-shadow: 3px 0 10px 0 rgb(29 29 31 / 10%), 15px 0 20px 0 rgb(29 29 31 / 10%);
  background-color: #ffffff;
  position: relative;
}
.left-tabs:after {
  position: absolute;
  content: '';
  top: 0px;
  bottom: 0;
  right: -1vw;
  height: 100%;
  border-top: 1.75vw solid #fff;
  border-right: 1vw solid transparent;
}
.tab-item {
  display: flex;
  align-items: center;
  padding: .35vw;
}
.tab-item.active-left {
  color: #4b83fc;
}
.tab-item.active-right {
  color: #4b83fc;
  text-decoration: underline;
}
.tab-item:hover {
  cursor: pointer;
}
.left-tabs .tab-item:last-child {
  padding-left: 0;
}
.left-tabs .tab-item:last-child:before {
  content: '';
  width: 1px;
  height: 1vw;
  background: #d8d8d8;
}
.tab-icon {
  width: .8vw;
  height: .8vw;
  margin: 0 8px;
}
.right-tabs {
  position: absolute;
  top: 0;
  right: 0;
}
.timeline-container {
  width: 100%;
  height: 3vw;
  border: 1px solid #f3f3f3;
  background-color: rgba(154, 162, 185, 0.05);
  margin: 0 10px;
}
.timeline-block {
  position: relative;
  width: calc((100% - 20px) / 21);
  height: 100%;
}
.timeline-block:nth-child(2n+1) {
  background-color: rgba(154, 162, 185, 0.05);
}
.timeline-block:nth-child(2n) {
  background-color: #f8fbff;
}
.timeline-block:after {
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  content: '';
  width: 1px;
  height: 100%;
  background: #848da7;
  opacity: .3;
}
.timeline-block:last-child:after {
  position: absolute;
  content: '';
  width: 0;
}
.year-block {
  position: absolute;
  bottom: -1.6vw;
  left: 0;
  font-size: 0.7vw;
}
.scale-block {
  position: relative;
  width: calc(100% / 12);
  height: 100%;
}
.scale-block:nth-child(2n+1):after {
  position: absolute;
  top: .6vw;
  bottom: .6vw;
  right: 0;
  content: '';
  width: 1px;
  background: #848da7;
  opacity: .2;
}
.scale-block:nth-child(2n):after {
  position: absolute;
  top: 1vw;
  bottom: 1vw;
  right: 0;
  content: '';
  width: 1px;
  background: #848da7;
  opacity: .2;
}
</style>
