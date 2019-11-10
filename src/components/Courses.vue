<template>
   <div id="courses-container">
        <h1 class="title">Courses</h1>
            <table id="courses">
                <thead>
                <tr>
                    <th>#</th>
                    <th>Course Title</th>
                    <th>Semester</th>
                    <th>Grade</th>
                </tr>
                </thead>
                <tbody>
                <tr v-for="(course, index) in courses"
                :key="index">
                <td>{{ index+1 }}</td>
                <td>{{ course.title }}</td>
                <td>{{course.semester}}</td>
                <td>{{ course.grade }}</td>
                </tr>
                </tbody>
                </table>
                        <br>
                        <br>
                        <div>
                            <button id="add-course-button" class="blue-button" v-on:click="isOpen = !isOpen">+</button>
                            <span v-show="isOpen" id="add-course-active">
                                <input class="input" type="text" placeholder="Course title" id="title" v-model="pealkiri">
                                <input class="input" type="number" min="1" max="8" placeholder="Semester" id="semester">
                                <input class="input" type="number" min="0" max="100" placeholder="Grade" id="grade">
                                <button v-on:click="send" class="green-button" id="save-course">Save</button>
                                <button v-on:click="isOpen = !isOpen" class="grey-button" id="cancel-course">Cancel</button>
                            </span>
                        </div>
                    </div>
</template>

<script>
import Course from "../classes/Course";
export default {
  name: "Courses",
    data: function() {
        return {
            courses: [
                    new Course("Algorithms and data structures", 3, 89),
                    new Course("Web application development", 3, 40),
                    new Course("Object oriented programming", 2, 95),
                    new Course("Underwater Basket Weaving", 3, 19),
                    new Course("Dog watching", 3, 100)
                ],
             isOpen: false,
            pealkiri: "",
    };
},
    methods: {
        toggle: function(){
            this.isOpen = !this.isOpen,
            this.pealkiri = ""
        },
        send: function () {
        }

    }
};
</script>

<style scoped>
</style>