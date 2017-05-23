<script>
import axios from 'axios';
import StudentLine from './StudentLine';
import AddStudent from './AddStudent';


export default {
  components: {
    StudentLine,
    AddStudent,
  },
  data() {
    return {
      students: [],
    };
  },
  methods: {
    getAll() {
      console.log('getAll');
      axios.get('http://localhost:3000/students')
        .then((response) => {
          console.log('getAll res', response);
          this.students = response.data;
        });
    },
    addOneO(students) {
      axios.post('http://localhost:3000/students', students)
        .then((res) => {
          this.students.push(res.data);
          console.log(res);
          console.log(students);
        });
    },
    remove(index) {
      axios.delete(`http://localhost:3000/students/${this.students[index].id}`)
        .then((res) => {
          this.students.splice(index, 1);
          console.log(res);
        });
    },
    editOne(value, index) {
      axios.put(`http://localhost:3000/students/${this.students[index].id}`, value)
         .then((res) => {
           this.students[index].firstname = res.data.firstname;
           console.log(this.students[index]);
         });
    },
  },
  mounted() {
    this.getAll();
  },
};
</script>

<template>
<div>
  <student-line v-for='(student, index) in students' :indexA='index' :student="student" v-on:remove="remove(index)" v-on:edit="editOne"></student-line>
  <add-student v-on:addOne="addOneO"></add-student>
</div>
</template>

<style>

</style>
