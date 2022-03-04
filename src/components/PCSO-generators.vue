<template>
    <div class="container">    
        <h1>{{title}}</h1>       
        <div class="submit">
         <button @click="generate(6, 1, 42);">Generate Numbers</button>      
       </div>
       <div id="numbers"></div>
    </div>
</template>
    
<script>    
      export default {
        data(){
             return{
              title:'My Lotto Generator',             
          }        
        },
        methods: {
         generate(size,lowest,highest){
               var numbers = [];
               for(var x = 0; x < size; x++) {var add = true;var randomNumber = Math.floor(Math.random() * highest) + 1;
		for(var y = 0; y < highest; y++) {
			if(numbers[y] == randomNumber) {
				add = false;}}
        if(add) {
			numbers.push(randomNumber);
		} else {
			x--;
		}
	}

var highestNumber = 0;
	for(var i = 0; i < numbers.length; i++) {
		for(var o = i + 1; o < numbers.length; o++) {
			if(numbers[o] < numbers[i]) {
				highestNumber = numbers[i];
				numbers[i] = numbers[o];
				numbers[o] = highestNumber;
			}
		}
	} 
	document.getElementById("numbers").innerHTML = numbers.join("    ");

          }
        }
      }
           
</script>    
<style lang="css">

h1{
    margin-top: -200px;
    margin-bottom: 40px;
    font-size: 36px;
    font-weight: normal;
    color: #000000;
    font-family: Arial, Helvetica, sans-serif;
}

button{
    padding-top: 10px;
    padding-bottom: 10px;
    padding-left: 10px;
    padding-right: 10px;
    border-radius: 5px;
    cursor:pointer;
    box-shadow: 0 4px 2px -2px gray;
}

.submit{
  margin-bottom:10px;
}

button:hover{
  background:#999;
  box-shadow: #999;
  color:#fff;
}
#numbers{
  font-size:30px;
  color:black;
  font-family: Arial, Helvetica, sans-serif;
}

</style>

