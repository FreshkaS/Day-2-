<template>
      <div class="notes">
    <div class="note" :class="{full:!grid}" v-for="(note , index) in notes" :key="index">
    <div class="note-header" :class="{full: !grid}">
    <p>{{note.title}}</p>
   <p style="cursor: pointer;" @click="removeNote(index)">x</p>
</div>
<div class="note-body">
    <p>{{note.descr}}</p>
    <span>{{note.date}}</span>
    </div>
</div>
    </div>
</template>
<script>
export default {
props:{
    notes:{
        type: Array,
        required: true
    }
},
grid:{
type: Boolean,
        required: true
},
methods:{
    removeNote(index){
        console.log(`Note id - ${index} removed`)
        this.$emit('remove ',index)
    }
}
}
</script>
<style lang="scss">
.notes{
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    padding: 40px 0;
}
.note{
    
    padding:18px 20px;
    margin-bottom: 20px;
    background-color: #ffff;
    &.full{
        width: 100%;
    }
}
.note-header{
    display: flex;
    align-items: center;
    justify-content: space-between;
    h1{
        font-size:32px ;
    }
    p{
        font-size:22px ;
        color: rgb(25, 0, 255);
    }
    svg{
       margin-right:12px ;
       color: #999999; 
       &.active{
           color: rgb(25, 0, 255);
       }
       &:last-child{
           margin-right:20px 0 ;
       }
    }
}
.note-body{
    p{
      margin:20px 0;  
    }
    span{
       font-size:14px ; 
       color: #999999;
    }
}



</style>