<template>
  <section>
    {{ headerSize }}
    <!-- mustache -->
  <div>{{ greet }} {{ name }}</div>
  <!-- html rendering from object script -->
  <div v-html="channel"></div>
  <div v-html="hack"></div>
  <h2 v-bind:id="headingId">Heading</h2>
  <button v-bind:disabled="isDisabled">Bind</button>
  <h2 class="underline">underline text</h2>
  <!-- v-bind -->
  <h2 class="underline" v-bind:class="statue">Status</h2>
  <h2 v-bind:class="isPromoted && 'promoted'">Promoted Moive</h2>
  <h2 v-bind:class="isSoldout ? 'sold-out' : 'new'">Soldout? Moive</h2>
  <h1 v-bind:class="['new' , 'promoted']">Newly promoted movie</h1>
  <h1 v-bind:class="[isPromoted && 'promoted', isSoldout ? 'sold-out' : 'new']">Newly promoted movie</h1>
  <h2 v-bind:class="{
    promoted: isPromoted,
    new: !isSoldout,
    'sold-out': isSoldout
  }">Object conditional movie</h2>
<h2 v-bind:style="{
  color: highlightColor,
  'font-size': headerSize + 'px'
}">Inline Style</h2>

<h2 v-bind:style="headerStyleObject">Style Object</h2>
<h2 v-bind:style="[baseStyleObject ,successStyleObject]">Success Style</h2>
<h2 v-bind:style="[baseStyleObject ,dangerStyleObject]">danger Style</h2>

<!-- if conditional rendering Example -->

<h2 v-if="num === 0">The number is zero</h2>
<h2 v-else-if="num < 0 ">The number is Negative</h2>
<h2 v-else-if="num > 0">the number is positive</h2>
<h2  v-else> not a number</h2>
<template v-if="display">
<h2>Youhok</h2>
<h2>Codebolution</h2>
<h2>Vue</h2>
</template>
<h2 v-show="showElement">V-show</h2>
<h2 v-if="showElement">V-If</h2>
<!-- list Rendering -->
<!-- Array of String -->
<h2 v-for="(name, index ) in names" :key="name">{{ index }}{{ name }}</h2>
<!-- Arrray of object -->
<h2 v-for="name in fulnames" :key="name.first">{{ name.first }} {{ name.last }}</h2>
<!-- Array of Array -->
<div v-for="actor in actors" :key="actor.name">
  <h2>{{ actor.name }}</h2>
  <h2 v-for="movie in actor.movies" :key="movie">{{ movie }}</h2>
</div>
<!-- add index and key -->

<h2 v-for="(value , index , key) in myInfo" :key="value">{{ index }} {{key}} {{ value }}</h2>
<!-- rendering block of Mutiple Element in the ui -->

<templete v-for="name in names" :key="name">
  <h2>{{ name }}</h2>
  <hr />
</templete>

<!-- conditional list Readering -->

<templet v-for="name in names" :key="name">
  <h2 v-if="name ==='Bruce'">{{ name }}</h2>
</templet>
<!-- Methods -->
<h2>{{ 2 + 3 + 5 }}</h2>
<h2>{{ 5 + 10 + 15 }}</h2>

<h2>Add method - {{ add(2 ,3 ,5) }}</h2>
<h2>Add method - {{ add(10 , 15 ,20) }}</h2>
<h2>Add method - {{ multiply(10) }}</h2>

<!-- Event handling -->
<!-- inline -->
<h2> {{ namess }}</h2>
<div>
  <button v-on:click="namess ='batman'">Changname</button>
  <button v-on:click="changName($event) , increment(1 ,$event)">ChangnameMethode</button>
</div>
<h2>{{ count }}</h2>
<div>
  <!-- <button v-on:click="count += 1">Increment</button>
  <button v-on:click="count -= 1">Decrement</button> -->
  <button v-on:click="increment(1)">Increment</button>
  <button v-on:click="Decrement(1)">Decrement</button>
</div>
<!-- form headling -->
<form @submit.prevent="submitForm">
  <pre>
    {{ JSON.stringify(formValues , null , 2) }}
  </pre>
  <div>
    <label for="name">
      Name
    </label>
    <input type="text" id="name" v-model.trim.lazy="formValues.name">

  </div>
  <div>
    <label for="profile" >Profile Summary</label>
    <textarea  id="profile" v-model="formValues.profileSummery" ></textarea>
  </div>
  <div>
    <label for="countey">Country</label>
    <select  id="country" v-model="formValues.country">
      <option value="">select a Country</option>
      <option value="india">India</option>
      <option value="Vietnam">Vietnam</option>
      <option value="singapore">singapore</option>
    </select>
  </div>

  <div>
    <label for="job-location">Job location</label>
    <select  id="job-location" multiple v-model="formValues.jobLocation">
      <option value="">select a Country</option>
      <option value="india">India</option>
      <option value="Vietnam">Vietnam</option> 
      <option value="singapore">singapore</option>
    </select>
  </div>

  <div>
    <input type="checkbox" id="remoteWork" v-model="formValues.remoteWork" true-value="yes" false-value="no"/>
    <label for="remoteWork">Open to remote work?</label>
  </div>

  <div>
    <label>Skill set</label>
    <input type="checkbox" id="html" value="html" v-model="formValues.skillSet"/>
    <label for="html">HTML</label>
    <input type="checkbox" id="css" value="css" v-model="formValues.skillSet"/>
    <label for="css">Css</label>
    <input type="checkbox" id="javascript" value="javascript" v-model="formValues.skillSet"/>
    <label for="javascript">JavaScript</label> 
    </div> 


    <div>
    <label>Year of Experience</label>
    <input type="radio" id="0-2" value="0-2" v-model="formValues.yearOfExperience"/>
    <label for="0-2">0-2</label>
    <input type="radio" id="3-5" value="3-5" v-model="formValues.yearOfExperience"/>
    <label for="3-5">3-5</label>
    <input type="radio" id="6-10" value="6-10" v-model="formValues.yearOfExperience"/>
    <label for="6-10">6-10</label> 
    </div> 
    <div>
      <label for="age">Age</label>
      <input @keyup.enter="submitForm" type="number" id="age" v-model.number="formValues.age">
    </div>
    <!-- <div>
      <button>Submit</button>
    </div> -->
</form>
<!-- bonus Directive -->
<h2 v-once>{{ username }}</h2>
<button @click="username = 'batman'">Chang name</button>
<h2 v-pre>{{ username }}</h2>
<!-- computed Properties -->
<h2>Fullname - {{ firstname }} {{ lastname }}</h2>
<h2>Fullname Computed {{ fullname }}</h2>
<button @click="changFullName">Changfullname</button>

<h2>Total -{{ item.reduce((total , curr) => (total = total + curr.price) , 0) }}</h2>
<button @click="item.push({ id:4 , title : 'keyboard' , price: 50})">Add item</button>
<h2>Computed Total - {{ total }}</h2>
<h2>Method Total -{{ getTotal() }}</h2>
<input type="text" v-model="country"/>
<template v-for="item in sellerItems" :key="item.id">
    <h2 v-if="item.price > 100"> {{ item.title }} {{ item.price }}</h2>
</template>
<h2 v-for="item in expensiveItems" :key="item.id">{{ item.title }} {{ item.price }}</h2>
<!-- watcher -->
<h2>Volume Tracker (0-20)</h2>
<h3>Current Volume - {{ volume }}</h3>
<button @click="volume += 2">Increase</button>
<button @click="volume -= 2">Decrease</button>
</section>
</template>

<script>




export default {
  name: 'App',
 data () {
   return {
    greet : 'Hello',
    name: 'badman',
    channel : '<b>Codevolution</b>',
    hack: `<a href="#" onclick="alert('you have been hacked!')">Win a prize</a>`,
    headingId: 'heading' ,
    isDisabled: false,
    statue:'success',
    isPromoted:true,
    isSoldout: true,
    highlightColor:'orange',
    headerSize:50,
    headerStyleObject: {
      color :'orange',
      fontSize: '50px',
      padding: '20px'
    },
    baseStyleObject :{
      fontSize : '50px',
      padding: '10px'
    },
    successStyleObject:{
      color :'green',
      backgroundColor: 'lightgreen',
      border: '1px solid green',
      padding:'20px'
    },
    dangerStyleObject:{
      color :'darkred',
      backgroundColor: 'red',
      border: '1px solid darkred',
      
    },
    //conditional Rendering
    num: 5,
    display: true,
    showElement: false,

    //list rendering
   names: ['Bruce', 'Clark' , 'Diana'],

   fulnames: [
    {first :'Bruce' , last: 'Wayne'},
    {first :'Clark' , last: 'Kent'},
    {first :'Princess' , last: 'Diana'}
   ],
    actors:[
      {
        name: 'Christian Bale',
        movies: ['Batman' , 'The Prestige'],
      },
      {
        name: 'Di Caprio',
        movies:['Titanic' , 'Inception'],
      }
    ],
    myInfo:{
      name:'hokiie',
      channal:'codevation',
      course: 'Vue 3'
    },

    //methode
    baseMulitplier:5,
    baseValue: 2 , 
     // Event handling
    namess: 'Hokieee',
    count: 0,
     //form healing
     formValues:{
      name: '',
      profileSummery: '',
      country: '',
      jobLocation: [],
      remoteWork : "no",
      skillSet: [],
      yearOfExperience:'',
      age: null,
     }, 
     // bonus Directive
     username: 'Vishwas',
     //computed properties
     firstname: 'Bruce',
     lastname:'Wayne',
     item:[
      {
        id:1,
        title:'TV',
        price:100
      },
      {
        id:2,
        title:'Phone',
        price:200
      },
      {
        id:3,
        title:'laptop',
        price:300
      }
     ],
     country: '',
     sellerItems:[
      {
        id:1,
        title:'TV',
        price:100
      },
      {
        id:2,
        title:'Phone',
        price:200
      },
      {
        id:3,
        title:'laptop',
        price:300
      }
     ],
     //watcher
     volume:0
   };
 },
 methods:{
  changName(event){
     this.namess = 'batman'
     console.log('Event' , event)
  },
  add(a , b ,c){
    return a+ b + c
  },
  multiply(num){
    return num * this.baseMulitplier
  },
  increment(num , event){
    this.count += num
    console.log(event)
  },
  Decrement(num){
    this.count -= num
  },
 //submitForm
 submitForm(){ 
  console.log('Form values' , this.formValues)
 },     
//
getTotal(){
  console.log('getTotal Method')
  return  this.item.reduce((total , curr) => (total = total + curr.price) , 0)
},
changFullName(){
  this.fullname = 'clark Kent'
}
 },
 computed:{
  fullname:{
    get(){
      return `${this.firstname} ${this.lastname}`
    },
    Set(value){
      const names = value.split(' ')
      this.firstname = names[0]
      this.lastname = names[1]
    }
  },
  // fullname (){
  //   return `${this.firstname} ${this.lastname}`
  // },
  total (){
    console.log('Total computed properties')
    return this.item.reduce((total , curr) => (total = total + curr.price) , 0)
  },
  expensiveItems(){
      return this.sellerItems.filter(item => item.price > 100)
  },
 
 },
 watch:{
  volume (newValue , oldValue){
    if ( newValue > oldValue && newValue === 16){
      alert('Listening to a high volume for a long time may damage your hearing')
    }
  }
}
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}

.underline{
  text-decoration: underline;
}

.promoted{
  font-style: italic;
}
.new{
  color: olivedrab;

}

.sold-out{
  color: red;
}

label {
  font-weight: bold;
  display: flex;
  margin-bottom:5 px ;
}
input + label {
  font-weight: bold;
  display: inline-flex;
  margin-right:20px ;
}

input[type= 'text'],
textarea,
select{
  display: block;
  width: 400px;
  padding: 6px 12px;
  font-size:14px;
  line-height: 1.42857143;
  color: #555;
  background-color: #fff ;
  background-image: none;
  border:1px solid #ccc;
  border-radius: 10px;
}
</style>
