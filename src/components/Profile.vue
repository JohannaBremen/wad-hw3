<template>
     <div id="profile-container">
            <div id="profile">
                <div class="avatar">
                    <img src="./../assets/me.png" id="picture" alt="My picture">
            </div>
            <div class="info">
                <ul>
                    <li id="name">{{ person.firstname }} {{ person.lastname }}</li>
                    <li id="birthdate">{{person.birthdate}}</li>
                    <li id="faculty">{{person.faculty}}</li>
                </ul>
            </div>
            <div id="gpa">
                <strong>{{person.gpa}}</strong>
            </div>
            <div class="clear-fix"></div>
        </div>
    </div>
</template>

<script>
import User from "../classes/User"

export default {
  name: "Profile",
  
    data: function() {
      return {
        person: new User('John', 'Doe', '11/10/1990', 'Software Engineering', 0)
      }
    },
  props: {
      gpa: Number
    },
    watch: {
      gpa: function (val) {
        this.person.gpa = val;
      }
    }
};
</script>

<style scoped>
</style>