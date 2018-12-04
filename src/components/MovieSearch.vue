<template>
<div>
    <input class="form-control mr-sm-2" @input="handleSearch" type="text" id="input" placeholder="Search" aria-label="Search">          
</div>         
</template>

<script>
export default {
   methods: {
       handleSearch(event){
           window.EventHub.$emit('search', event.target.value);
       }
   }
}
</script>
