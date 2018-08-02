<template>
  <section class="mid">
    <div class="basics" v-for="(item,index) in skills" :key="index">
      <div class="bg" v-show="(index + 1) !== skills.length">
        <div class="rect" :style="{height: checkIsAllCompleted(item) ? 'calc(100% - 27px)' : '0px'}"></div>
        <div class="triangle"></div>
      </div>
      <div class="thumb">
        <img :src="item.img" alt="">
      </div>
      <div class="skills">
        <div class="skill" v-for="(skill, sindex) in item.skill" :key='sindex'>
          <div class="icon" :class="{focus: skill.name === nowFocus, done: checkIsAllSelected(skill)}" @click="focus(skill)">
            <i class="material-icons">{{ skill.icon }}</i>
          </div>
          <div class="val">
            <p>
              <i class="material-icons">settings</i>
              <span>{{learn(skill).recommened_length}}</span>/{{skill.recommened.length}}
            </p>
            <p>
              <i class="material-icons">filter_tilt_shift</i>
              <span>{{learn(skill).optional_length}}</span>/{{skill.optional.length}}
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Mid',
  props: ['skills', 'nowFocus'],
  methods: {
    focus: function(skill) {
      skill.selected = !skill.selected;
      this.$emit('changeNowSelected', skill.name);
    },
    learn(skill) {
      let learn_num = {
        recommened_length: skill.recommened.filter(rc => rc.selected === true).length,
        optional_length: skill.optional.filter(rc => rc.selected === true).length
      }
      return learn_num;
    },
    // 確認全部都被選擇了
    checkIsAllSelected(skill) {
      let flag = true;
      if(skill.recommened.some(item => !item.selected) || 
        skill.optional.some(item => !item.selected)) {
          flag = false;
      }
      return flag;
    },
    // 確認該星球的技能都完成
    checkIsAllCompleted(item) {
      let flag = true;
      let skills = item.skill;
      for (let i = 0; i < skills.length; i++) {
        if(skills[i].recommened.some(item => !item.selected) || 
          skills[i].optional.some(item => !item.selected)) {
            flag = false;
        };
      }
      item.all_completed = flag;
      return flag;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='scss'>
@import '../style/components/mid.scss';
</style>
