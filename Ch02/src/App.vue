<template>
  <h3>Ch02.Vue Directive 실습</h3>
  <h4>1)v-text</h4>
  <p v-text="tit1"></p>
  <p {{ tit2 }}></p>
  <hr/>
  <h4>2)v-show</h4>
  <p v-show="result1">show directive1</p>
  <p v-show="result2">show directive2</p>
  <hr/>
  <h4>3)v-if</h4>
  <p v-if="result1">if directive1</p>
  <p v-if="result2">if directive2</p>
  <p v-else>if directive3</p>

  <p v-if="score >=90">A 입니다</p>
  <p v-else-if="score >=80">B 입니다</p>
  <p v-else-if="score >=70">C 입니다</p>
  <p v-else-if="score >=60">D 입니다</p>
  <p v-else-if="score >=90">F 입니다</p>
  
  <p v-if="tit3">{{ tit3 }}</p>
  <p v-else>tit empty...</p>
  <hr/>
  <h4>4)v-for</h4>
  <ul>
    <li v-for="i in 3">i:{{ i }}</li>
  </ul>
  <ul>
    <li v-for="city in cities">{{ city }}</li>
  </ul>

  <table>
    <tr>
      <th>아이디</th>
      <th>이름</th>
      <th>나이</th>
    </tr>
    <tr v-for="person in persons">
        <td>{{person.uid}}</td>
        <td>{{person.name}}</td>
        <td>{{person.age}}</td>
    </tr>
  </table>
  <hr/>

  <h4>5)v-on</h4>
  <h4>click</h4>
  <button v-on:click="handler1">button1</button>
  <button v-on:click="handler2(10)">button2</button>
  <button>button3</button>

  <h4>count 예제</h4>
  <p>{{ count }}</p>
  <button v-on:click="countHandler">카운터</button>
  
  <h4>change 예제</h4>
  <select v-on:change="changeHandler" name="" id="">
    <option value="">서울</option>
    <option value="">대전</option>
    <option value="">대구</option>
    <option value="">부산</option>
    <option value="">광주</option>
  </select>

  <h4>submit 예제</h4>
  <form v-on:submit.prevent="submitHeandler1">
    <table border="1">
      <tr>
        <td>아이디</td>
        <td><input type="text" name="uid"></td>
      </tr>
      <tr>
        <td>이름</td>
        <td><input type="text" name="name"></td>
      </tr>
      <tr>
        <td>나이</td>
        <td><input type="text" name="age"></td>
      </tr>
      <tr>
        <td>주소</td>
        <td>
          <select name="addr1" id="">
            <option value="">서울</option>
            <option value="">대전</option>
            <option value="">대구</option>
            <option value="">부산</option>
            <option value="">광주</option>
          </select>
        </td>
      </tr>
      <tr>
        <td colspan="2" align="right">
          <input type="submit" value="전송">
        </td>
      </tr>
    </table>
  </form>
  <hr/>

  <h4>6)v-bind</h4>
  <img v-bind:src="path1"/>
  <img v-bind:src="path2"/>
  
  <a :href="url1">네이버</a>
  <a :href="url2">구글</a>

  <button @click="oneClick" v-bind:disabled="isActive">한번만 클릭되는 버튼</button>
  
  <hr/>

  <h4>7)v-model</h4>
  <h4>input</h4>
  <p>이름 : {{ name }}</p>
  <input type="text" v-model="name" placeholder="이름입력">

  <h4>textarea</h4>
  <p>{{ message }}</p>
  <p>문자수 : {{  message.length}}</p>
  <textarea v-model="message" name="" id="" cols="30" rows="10">
  
  
  </textarea>

  <p>checkout</p>
  <p>
    <input type="checkbox" v-model="inChecked">
    체크상태 : {{isChecked }}
  </p>

  <p>
    <label for=""><input type="checkbox" value="등산" v-model="hobbies">등산</label>
    <label for=""><input type="checkbox" value="등산" v-model="hobbies">영화</label>
    <label for=""><input type="checkbox" value="등산" v-model="hobbies">독서</label>
    <label for=""><input type="checkbox" value="등산" v-model="hobbies">운동</label>
    <label for=""><input type="checkbox" value="등산" v-model="hobbies">게임</label>
    <br>
    선택값: {{ hobbies }}
  </p>

  <h4>select</h4>
  <select v-model="country">
    <option value="">한국</option>
    <option value="">미국</option>
    <option value="">일본</option>
    <option value="">중국</option>
    <option value="">호주</option>
  </select>
  <p>선택값 : {{ country }}</p>

  <h4>form</h4>
  <form v-on:submit.prevent="submitHeandler2">
    <table border="1">
      <tr>
        <td>아이디</td>
        <td><input type="text" v-model="user.uid"></td>
      </tr>
      <tr>
        <td>이름</td>
        <td><input type="text" v-model="user.name"></td>
      </tr>
      <tr>
        <td>나이</td>
        <td><input type="text" v-model="user.age"></td>
      </tr>
      <tr>
        <td>주소</td>
        <td>
          <select name="addr1" v-model="user.addr">
            <option value="">서울</option>
            <option value="">대전</option>
            <option value="">대구</option>
            <option value="">부산</option>
            <option value="">광주</option>
          </select>
        </td>
      </tr>
      <tr>
        <td colspan="2" align="right">
          <input type="submit" value="전송">
        </td>
      </tr>
    </table>
  </form>
  <hr/>
</template>

<script>


export default {
  name: 'App',
  data(){
    return{
      tit1:"Hello",
      tit2:"welcome",
      tit3:"",
      result1: true,
      result2: false,
      score:86,
      cities:["서울","대전","대구","부산","광주"],
      persons:[
        {uid:"a101", name:"김유신", ahe:23},
        {uid:"a102", name:"김춘추", ahe:21},
        {uid:"a103", name:"장보고", ahe:33},
        {uid:"a104", name:"강감찬", ahe:43},
        {uid:"a105", name:"이순신", ahe:53},
      ],
      count:0,
      path1:"/img/flower1.jpg",
      path2:"/img/flower2.jpg",
      url1:"https://www.naver.com/",
      url2:"https://www.google.com/",
      isActive:false,
      name:"홍길동",
      message:"",
      isChecked:false,
      hubbies:[],
      country:"한국",
      user:{
          uid:"",
          name:"",
          age:"",
          addr:""
      }
    };
  }, //date end
  methods: {
    handler1 : function(){
      alert("button1 click!!!");
    },
    handler2: function(value){
      alert("button2 click:" + value);
    },
    handler3:function(e){
      alert("button3 click:" + e);
    },
    countHandler:function(){
      this.count++;
    },
    changeHandler: function(e){
      
      alert(e.target.value);
    },
    submitHeandler1:function(e){
      let uid = e.target.elements.uid.value;
      let name = e.target.elements.uid.value;
      let age = e.target.elements.uid.value;
      let addr = e.target.elements.uid.value;

      console.log("uid:" + uid);
      console.log("uid:" + name);
      console.log("uid:" + age);
      console.log("uid:" + addr);
    },

    submitHeandler2:function(e){
      console.log("uid:" + this.user.uid);
      console.log("uid:" + this.user.name);
      console.log("uid:" + this.user.age);
      console.log("uid:" + this.user.addr);
    },
    onclick:function(){
      alert('한번만 클릭할수 있습니다.');
      this.isActive = true;
    }
  }, //method end
};
</script>
