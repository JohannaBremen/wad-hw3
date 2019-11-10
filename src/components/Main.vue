<template>
    <section id="container">
            <section id="main">
                <div class="content">
                   <Profile :class="this.profileTabActive ? 'tab-active' : 'tab'"/>
                   <Courses :class="this.coursesTabActive ? 'tab-active' : 'tab'"/>
                </div>
                <div class="controls">
                    <button id="profile-button" :class="this.profileTabActive ? 'pill active' : 'pill'" @click="toggleProfile">Profile</button>
                    <button id="courses-button" :class="this.coursesTabActive ? 'pill active' : 'pill'" @click="toggleCourses">Courses</button>
                </div>
            </section>
        </section>
</template>

<script>
import Profile from "./Profile.vue";
import Courses from "./Courses.vue";

export default {
  name: "Main",
  components: {
    Profile,
    Courses,
  },
 data: () => {
    return {
      profileTabActive: true,
      coursesTabActive: false
    };
  },
  methods: {
    toggleProfile: function() {
      this.profileTabActive = true;
      this.coursesTabActive = false;
    },
    toggleCourses: function() {
      this.profileTabActive = false;
      this.coursesTabActive = true;
    }
  }
  
};
</script>

<style scoped>
</style>