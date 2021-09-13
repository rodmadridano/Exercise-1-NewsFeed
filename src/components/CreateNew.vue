<template>
  <form @submit.prevent="addNews">
     <label>Title :</label>
     <input type="title" required v-model="title"> 
     <label>Content :</label>
     <input type="content" required v-model="content"> 
     <div class="submit">
      <button name="button">Submit</button>
    </div>
  </form>
  <hr>
  <div id="cardApp"> 
    <div v-for="(news, index) in newslist" :key="news" class="card">
      <div class="card-body">
        <p><b>Title : </b><span> {{news.title}} </span></p>
        <p><b>Content : </b><span> {{news.content}} </span></p>
      </div>   
      <div class="card-footer">
        <button type="button">View</button>          
        <button @click="showMessageBox=true">Delete</button>        
        <!-- <div v-if="isConfirm=true">
           <button @click.capture="removeNews(index)"></button> 
        </div> -->
        <!-- <button @click="removeNews(index)">Delete</button>    -->
      </div>      
    </div>		
  </div>

<!-- <MessageBox :show="showMessageBox"
            :cancel="cancelNews"
            :confirm="confirmdelete"
            @close="removeNews(index)"
            title="Delete a Title?"
            description="Are you sure you want to delete this?"/>    -->

</template>

<script>
import { ref } from '@vue/reactivity';
import MessageBox from './MessageBox.vue';

export default {
  setup() {
    const title = ref('')
    const content = ref('')
    const id = ref(null)

    const addNews = () => {
        newslist.push({id: id.value, title: title.value, content: content.value}),
        title.value = '',
        content.value = ''
      }
    const removeNews = (index) => {
        newslist.splice(index, 1),
        showMessageBox = false
      }

    return {title, content, id, addNews, removeNews}
  }

  // data() {
  //   return {
  //     showMessageBox: false,
  //     isConfirm: false,
  //     index: '',
  //     title: '',
  //     content: '',
  //     newslist: []
  //   }
  // },
  // components: {
  //   MessageBox
  // },
  // methods: {
  //   addNews() {
  //     this.newslist.push({index: this.index, title: this.title, content: this.content}),
  //     this.title = '',
  //     this.content = ''
  //   },
  //   removeNews(index) {
  //     this.newslist.splice(index, 1),
  //     this.showMessageBox = false
  //   },    
  //   confirmdelete() {
  //     this.showMessageBox = false,
  //     this.isConfirm = true
  //   },    
  //   cancelNews() {
  //     this.showMessageBox = false
  //   }
  // }
}
</script>

<style>
  form {
      max-width: 620px;
      margin: 10px auto;
      background: white;
      text-align: left;
      padding: 40px;
      border-radius: 10px;
  }
  label {
      color: #aaa;
      display: inline-block;
      margin: 25px 0 15px;
      font-size: 0.9em;
      text-transform: uppercase;
      letter-spacing: 1px;
      font-weight: bold;
  }
  input {
      display: block;
      padding: 10px 6px;
      width: 600px;
      box-sizing: border-box;
      border: none;
      border-bottom: 1px solid #ddd;
      color: #555;
      background: rgb(238, 234, 234);
  }
  button {
      background: #0b6dff;   
      border: 0;
      padding: 10px 20px;
      margin-top: 20px;
      color: white;   
      width: 100px;
      border-radius: 20px;
  }
  .submit {
      text-align: center;
  }
 #cardApp {
   display: flex; 
   flex-wrap: wrap;
   text-align: left;

 }
 .card {
    text-align: left;   
    background-color: rgb(212, 201, 201);
    background-clip: border-box;
    border: 1px solid rgba(0,0,0,.125);
    margin-bottom: 5px;     
    margin-left: 5px;     
    width: 350px;
    height: 250px auto;
    border-radius: 20px;
    padding: 40px;
    margin-top: 1px;     
    box-sizing: border-box;    
 }
 .card-body {
   display: block;
   /* word-wrap: break-word; */
 }
 .card-body p{
   display: block;
   word-wrap: break-word;
 }
 .card-footer {
   display: block;
   text-align: right;   
} 
 .card-footer button{
   margin-left: 5px;
} 
   
</style>