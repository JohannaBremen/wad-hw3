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
                                <input v-model="input.title" class="input" id="title" placeholder="Course title" type="text">
                                <input v-model="input.semester" class="input" id="semester" max="8" min="1" placeholder="Semester" type="number">
                                <input v-model="input.grade" class="input" id="grade" max="100" min="0" placeholder="Grade" type="number">
                                <button @click="send" class="green-button" id="save-course">Save</button>
                                <button @click="cleanInput" class="grey-button" id="cancel-course">Cancel</button>
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
            input: {},
            pealkiri: "",
    };
},
    methods: {
        toggle: function(){
            this.isOpen = !this.isOpen,
            this.pealkiri = ""
        },

        send: function () {
            this.courses.push(new Course(this.input.title, this.input.semester, this.input.grade));
            this.cleanInput();
        },

        cleanInput: function () {
                this.input = {};
                this.toggle();
            },

    },
    created() {
            this.$emit("changedCourses", this.courses);
        },
    watch: {
            courses: function () {
                this.$emit("changedCourses", this.courses);
            }
        }
};
</script>

<style scoped>
</style>