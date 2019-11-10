<template>
    <section id="container">
            <section id="main">
                <div class="content">
                   <Profile :gpa="gpa" :class="this.profileTabActive ? 'tab-active' : 'tab'"/>
                   <Courses @changedCourses="changedCourses" :class="this.coursesTabActive ? 'tab-active' : 'tab'"/>
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
      coursesTabActive: false,
      courses: []
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
    },
    changedCourses: function(val){
      this.courses = val;
    }
  },
  computed: {
            gpa: function () {
                return Math.round(this.courses.reduce(function (total, c) {
                    return total + (c.grade > 60 ? Math.floor((c.grade - 51) / 10) : c.grade > 50 ? 0.5 : 0)
                }, 0) / this.courses.length * 100) / 100
            }
        }
  
};
</script>

<style scoped>
</style>