<template>
  <form @submit.prevent="submitForm">
    <div class="form-control">
      <label class="emp-name">ชื่อพนักงาน</label>
      <input type="text" class="form-input" v-model.trim="employee.name" />
    </div>
    <div class="form-control">
      <label class="emp-salary">เงินเดือน</label>
      <input type="number" class="form-input" v-model="employee.salary" />
    </div>
    <div class="form-control">
      <label class="emp-department">ตำแหน่งงาน</label>
      <select class="form-input" v-model="employee.department">
        <option value="ฝ่ายการตลาด">ฝ่ายการตลาด</option>
        <option value="ฝ่ายการเงิน">ฝ่ายการเงิน</option>
        <option value="ฝ่ายขาย">ฝ่ายขาย</option>
        <option value="ฝ่ายไอที">ฝ่ายไอที</option>
      </select>
    </div>
    <div class="form-control">
      <h2>เพศ</h2>
      <div>
        <input type="radio" v-model="employee.gender" value="ชาย" />
        <label for="gender-name">ชาย</label>
      </div>
      <div>
        <input type="radio" v-model="employee.gender" value="หญิง" />
        <label for="gender-name">หญิง</label>
      </div>
    </div>
    <div class="form-control">
      <h2>ทักษะด้านภาษา</h2>
      <div>
        <input type="checkbox" v-model="employee.skill" value="ภาษาอังกฤษ" />
        <label for="skill">ภาษาอังกฤษ</label>
      </div>
      <div>
        <input type="checkbox" v-model="employee.skill" value="ภาษาไทย" />
        <label for="skill">ภาษาไทย</label>
      </div>
      <div>
        <input type="checkbox" v-model="employee.skill" value="ภาษาญี่ปุ่น" />
        <label for="skill">ภาษาญี่ปุ่น</label>
      </div>
      <div>
        <input type="checkbox" v-model="employee.skill" value="ภาษาจีน" />
        <label for="skill">ภาษาจีน</label>
      </div>
    </div>
    <div>
      <button>บันทึกข้อมูล</button>
    </div>
  </form>
</template>

<script>
export default {
  name: "FormComponent",
  data() {
    return {
      employee: {
        name: "",
        salary: null,
        department: "ฝ่ายการตลาด",
        gender: "",
        skill: ["ภาษาไทย"],
      },
    };
  },
  methods: {
    submitForm() {
      const newEmployee = {
        name: this.employee.name,
        salary: this.employee.salary,
        department: this.employee.department,
        gender: this.employee.gender,
        skill: this.employee.skill,
      };
      this.$emit("save", newEmployee);
      this.resetForm()
    },
    resetForm() {
      this.employee.name = "";
      this.employee.salary = null;
      this.employee.department = "ฝ่ายการตลาด";
      this.employee.gender = "";
      this.employee.skill = [];
    },
  },
};
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.25);
  padding: 2rem;
  background: #fff;
}
.form-control {
  margin: 0.5rem 0;
}
label {
  font-weight: bold;
}
input select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}
button {
  font: inherit;
  background: orangered;
  color: white;
  cursor: pointer;
  padding: 0.5rem 1rem;
  border-radius: 15px;
}
.form-input {
  width: 100%;
  height: 30px;
}
input[type="radio"],
input[type="checkbox"] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}
input[type="radio"] + label,
input[type="checkbox"] + label {
  font-weight: normal;
}
h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}
</style>
