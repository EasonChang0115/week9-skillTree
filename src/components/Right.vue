<template>
  <section class="right">
    <div class="contain">
      <div class="top">
        <i class="material-icons">{{nowSkill.icon}}</i>
        <p>{{nowSkill.name}}</p>
      </div>
      <div class="bottom">
        <div class="recommend" v-if="nowSkill.recommened.length">
          <i class="material-icons">settings</i>
          <p>RECOMMENDED</p>
          <span v-for="(item, index) in nowSkill.recommened"
                :class="{'selected':item.selected}"
                @click="skillChange(item)"
                :key="index">{{item.rc_skill}}</span>
        </div>
        <div class="option" v-if="nowSkill.optional.length">
          <i class="material-icons">filter_tilt_shift</i>
          <p>OPTIONAL</p>
          <span v-for="(item,index) in nowSkill.optional"
                :class="{'selected':item.selected}"
                @click="skillChange(item)"
                :key="index">{{item.op_skill}}</span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Right',
  props: ['nowSkill'],
  methods: {
    skillChange(item) {
      item.selected = !item.selected;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='scss'>
@import '../style/components/right.scss';
</style>
