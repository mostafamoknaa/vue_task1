<template>
  <div class="container">
    <HeaderComponent />

    <div class="main-content">
      <AppSidebar />
      <div class="content">
        <button @click="showModal = true" class="add-btn">Add</button>
        <table>
          <thead>
            <tr>
              <th>ID</th><th>Name</th><th>City</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="student in students" :key="student.id">
              <td>{{ student.id }}</td>
              <td>{{ student.name }}</td>
              <td>{{ student.city }}</td>
            </tr>
          </tbody>
          <tfoot>
            <tr>
              <td colspan="3">Total Number Of Students {{ students.length }}</td>
            </tr>
          </tfoot>
        </table>
      </div>
    </div>

    <div v-if="showModal" class="modal">
      <div class="modal-box">
        <h3>Add Student</h3>
        <input v-model="newStudent.id" placeholder="ID" />
        <input v-model="newStudent.name" placeholder="Name" />
        <input v-model="newStudent.city" placeholder="City" />
        <div class="btn-group">
          <button @click="addStudent">OK</button>
          <button @click="showModal = false">Cancel</button>
        </div>
      </div>
    </div>

    <FooterComponent />
  </div>
</template>


<script>
import FooterComponent from './components/FooterComponent.vue';
import HeaderComponent from './components/HeaderComponent.vue';
import AppSidebar from './components/AppSidebar.vue';

export default {
  components: {
  HeaderComponent,
  FooterComponent,
  AppSidebar
  
},
  data() {
    return {
      showModal: false,
      newStudent: { id: '', name: '', city: '' },
      students: [
        { id: 100, name: 'samir', city: 'minya' },
        { id: 200, name: 'ahmed', city: 'cairo' },
        { id: 300, name: 'mohamed', city: 'alex' },
        { id: 400, name: 'moustafa', city: 'mahala' },
      ]
    };
  },
  methods: {
    addStudent() {
      if (this.newStudent.id && this.newStudent.name && this.newStudent.city) {
        this.students.push({ ...this.newStudent });
        this.newStudent = { id: '', name: '', city: '' };
        this.showModal = false;
      }
    }
  }
};
</script>

<style>
.container {
  padding: 20px;
  font-family: Arial, sans-serif;
  display: flex;
  flex-direction: column;
}

.main-content {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}

.content {
  flex: 1; 
  margin-left: 20px;
}

.add-btn {
  background: steelblue;
  color: white;
  padding: 8px 15px;
  border: none;
  margin-bottom: 10px;
  cursor: pointer;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid #444;
  padding: 10px;
  text-align: left;
}

tfoot {
  background-color: #f2f2f2;
  font-weight: bold;
}

.modal {
  position: fixed;
  top: 0; left: 0; right: 0; bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-box {
  background: white;
  padding: 20px;
  border-radius: 8px;
  width: 300px;
}

.modal-box input {
  display: block;
  margin-bottom: 10px;
  width: 100%;
  padding: 8px;
}

.btn-group {
  display: flex;
  justify-content: space-between;
}

</style>
