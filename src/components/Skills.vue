<template>
  <div class="holder">
    <div>
      <form @submit.prevent="addSkill">
        <input
          type="text"
          placeholder="Enter a skill..."
          v-model="skill"
          v-validate="'min:5'"
          name="skill"
        >
        <transition
          name="alert-in"
          enter-active-class="animated flipInX"
          leave-active-class="animated flipOutX"
        >
          <p class="alert" v-if="errors.has('skill')">{{errors.first('skill')}}</p>
        </transition>
      </form>
      <!-- {{skill}} -->
      <!-- <input type="checkbox" id="checkbox" v-model="checked"> -->
      <ul>
        <transition-group
          name="list"
          enter-active-class="animated bounceInUp"
          leave-active-class="animated bounceOutDown"
        >
          <li v-for="(data, index) in skills" :key="index">
            {{index}}. {{data.skill}}
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
          </li>
        </transition-group>
      </ul>
      <p>my skillz</p>
      <!-- <div v-bind:style="{backgroundColor: bgColor, width: bgWidth, height: bgHeight}"></div> -->
      <!-- <div v-bind:class="alertObject"></div> -->
      <!-- <div v-bind:class="{alert: showAlert, 'another-class': showClass}"></div> -->
      <!-- <p v-if="skills.length >= 1">ssss</p> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "Skills",
  data() {
    return {
      // checked: false,
      skill: "",
      skills: [{ skill: "JS" }, { skill: "Photoshop" }, { skill: "React" }]
      // bgColor: "yellow",
      // bgWidth: "100%",
      // bgHeight: "30px"
      // alertObject: { alert: true, "another-class": true }
      // showAlert: true,
      // showClass: true
    };
  },
  methods: {
    addSkill() {
      this.$validator.validateAll().then(result => {
        if (result) {
          this.skills.push({
            skill: this.skill
          });
          this.skill = "";
          // console.log("is checked? " + this.checked);
        } else {
          console.log("invalid");
        }
      });
    },
    remove(id) {
      this.skills.splice(id, 1);
    }
  }
};
</script>

<style src="./Skills.css" scoped>
</style>
