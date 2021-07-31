<template>
    <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" v-model="text" name="text" placeholder="Add Task" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
        type="text"
        v-model="day"
        name="day"
        placeholder="Add Day & Time"
      />
    </div>
    <div class="form-control">
      <label>Importance</label>
      <i @click="setRating(1)" class="fa fa-star" aria-hidden="true"></i>
      <i @click="setRating(2)" :class="[ratings >= 2 ? 'fa-star fa' : 'fa-star far']" aria-hidden="true"></i>
      <i @click="setRating(3)" :class="[ratings >= 3 ? 'fa-star fa' : 'fa-star far']" aria-hidden="true"></i>
      <i @click="setRating(4)" :class="[ratings >= 4 ? 'fa-star fa' : 'fa-star far']" aria-hidden="true"></i>
      <i @click="setRating(5)" :class="[ratings >= 5 ? 'fa-star fa' : 'fa-star far']" aria-hidden="true"></i>
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>

export default {
  name: 'AddTask',
  data(){
    return{
      text: '',
      day: '',
      reminder: false,
      ratings: 1,
    }
  },
  methods: {
    setRating(rating){
      this.ratings = rating
    },
    onSubmit(e){
      e.preventDefault()

      if(!this.text){
        alert('Please add a task')
        return
      }

      const newTask = {
        id: Math.floor(Math.random() * 100000),
        text: this.text,
        day: this.day,
        reminder: this.reminder,
        ratings: this.ratings,
      }

      this.$emit('add-task', newTask)

      this.text = ''
      this.day = ''
      this.reminder = false
      this.ratings = 1
    },
  },
}
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>