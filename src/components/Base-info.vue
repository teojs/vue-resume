<template>
  <div class="baseInfo">
    <ul>
      <li>
        <h1><i class="iconfont icon-baseinfo ib"></i>基本信息：</h1>
      </li>
      <li v-for='(item, index) in baseInfo' :key="index">
        <div class="flex-box">
          <div class="flex-cell"><span><i class="iconfont ib"
                :class='"icon-" + item.iconName'></i>{{item.infoName}}</span></div>
          <div class="flex-cell">
            <a :href='item.url' target="_blank" v-if='item.url'><i
                class="iconfont icon-wailian ib"></i>{{item.value}}</a>
            <span v-else>{{item.value}}</span>
          </div>
        </div>
      </li>
    </ul>
    <ul>
      <li>
        <h1><i class="iconfont icon-skill ib"></i>职业技能：</h1>
      </li>
      <li class="tags">
        <div class="tag" v-for='(item, index) in skills' :key="index">{{item}}</div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'baseInfo',
  data () {
    return {}
  },
  props: [
    'baseInfo',
    'skills'
  ]
}
</script>
<style lang="scss">
.tags {
  // display: flex;
  // justify-content: space-between;
  // flex-wrap: wrap;
  .tag {
    display: inline-block;
    margin: 10px 5px;
    padding: 5px 10px;
    border-radius: 99px;
    border: 1px solid #ffffff;
    font-size: 14px;
  }
}
</style>
