<template>
<div id="app">
    

        <form id="app" @submit.prevent="checkForm">
<div>



            <p v-if="errorNameEmpty" class="textError">nome não pode estar vazio</p>
            <p v-if="errorNameLenght"></p>
</div>

        <div>
    
            </div>


</form>     
</div>
    
</template>

<script>


export default {


name: "Texts",

props: {
    dados: {
    type: String,
    required: true,
    },
},
};
</script>
