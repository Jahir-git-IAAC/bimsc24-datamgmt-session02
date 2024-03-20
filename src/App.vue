<!-- the script is where the js code goes -->
<script setup>
import { onMounted, ref } from "vue" // you need this to use ref()

  //Change background color
  const doc = document.documentElement;
  doc.style.background = "#2b2e2e";
  doc.style.fontFamily = "monospace";
  
  var makeBackgroundDark = null;
  var makeBackgroundBright = null;


onMounted(() => {
    makeBackgroundDark= () =>{
    doc.style.background = '#2b2e2e';
    let mainb = document.getElementById("main")
    mainb.style.borderColor = '#dae6e4';
    mainb.style.webkitTextFillColor = '#fcfcfc';
    let titleb = document.getElementById("title")
    titleb.style.webkitTextFillColor = '#fcfcfc';
    
}
 makeBackgroundBright = () =>{
    doc.style.background = "#fcfcfc";
    let mainb = document.getElementById("main")
    mainb.style.borderColor = '#000000';
    mainb.style.webkitTextFillColor = '#000000';
    let titleb = document.getElementById("title")
    titleb.style.webkitTextFillColor = '#000000';
}


})

// main text adding 
const mainTxt = ref("");
const textInput = ref("");
function addToMainTxt() {
   mainTxt.value += textInput.value;
}

// coloring 
const colorMain = ref("")
const colorInput = ref("");
const divNameInput = ref("")
var changecolor = null

// using this function to insure the DOM is loaded before fire the fuction . 
// also the function syntax is diffrent 
onMounted(() => {
    changecolor = () =>{
        let mySelectedDiv = document.getElementById(divNameInput.value)
        mySelectedDiv.style.background = colorInput.value
        console.log(mySelectedDiv);
    };

})

</script>



<!-- the template is where the html code goes -->
<template>

<div id="navbar" class="container">  
        <div id="title"  >
            CBDM assignment 02
        </div>
        <div id="logo">
            <img src="./ComfyUI_00043_.png" alt="profilepic">
        </div>
    </div>
    <div id="maincontainer" >
    <div id="main" class="container" ><h2>Main</h2>
            <br/>
            <p>{{mainTxt}}</p>
            </div>
        </div>
    <div id="flex">
        <div id="sidebar" class="container">
            <h1> Sidebar </h1>
            <br/>
            <h3> change background color! </h3>
            <button @click="makeBackgroundDark">
                Dark background
            </button>
            <br/>
            <button @click="makeBackgroundBright">
                Bright background
            </button>
            <br/>
            <h3> Infinity text adding </h3>
            <input class="inputbox" v-model="textInput" type="text" placeholder="write here!">
            <button @click="addToMainTxt">
                Add text here to show it inside "Main"
            </button>
           


        </div>
        
    </div>


</template>



<!-- style is where the css code goes -->
<style scoped>


body{
    margin:0;
}

div{

    /* put the borders in the inside of container */
    box-sizing: border-box;
}

img{

    height: 95%;
    width: auto;
    margin: 5px;
}


.container{
    width: 100%;
    float: right;
    border-width: 1px;
}

#navbar{
    width: calc(98% - 250px);
    height: 50px;
    border-color: rgb(34, 34, 34);
    border-style: hidden;
    float: right;
    box-sizing: border-box;
}

#title{
    color: #201b20;
    width: 70%;
    float:left;
    font-size: 18px;
    font-weight: bolder;
    padding: 15px;
}

#logo{
    width: 30%;
    height: 100%;
    float: right;
    text-align: right;
}

#maincontainer{
    width: calc(98% - 250px);
    height: calc(100vh - 50px );;
    float:right;
    border-color: rgb(235, 248, 248);
    text-align: right;

}
#main{
    width: 98%;
    word-break:break-all;
    border-color: #012413;
    color: #021b19;
    font-size:xx-large;
    height: calc(99%);
    border-style: groove;
    border-radius: 20px;
    text-align: center;
    padding: 10px;
    margin-inline: 1%;

}

#flex{
    width: 285px;
    display: flex;
    height: calc(100vh);
}

#sidebar{
    border-color: #6c7271;
    border-width : 3px;
    border-style: solid;
    width: 280px;
    border-radius: 20px;
    background-color: rgb(31, 32, 32);
    margin: 48px 0px 5px 5px ;
    text-align: center;
    box-sizing: border-box;
    padding: 10%;


}






.inputbox{
    width: 95%;
    text-align: center;
    margin: auto;
    align-items: center;
}
</style>


