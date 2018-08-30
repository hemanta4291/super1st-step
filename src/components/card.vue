<template>

    <ul class="list-group">
            <li class="list-group-item">
            <span>name</span>
            <span class="float-right">price</span>
            </li>

            <li v-for="(item, index) in items" :key="index" class="list-group-item">
            <button @click="remove(index)">remove</button>
            <span>{{item.title}}</span>
            <span class="float-right">{{item.id}}</span>
            </li>

            <li class="list-group-item">
            <span>total</span>
            <span class="float-right">${{totalprice}}</span>
            </li>

          </ul>
</template>

<script>
export default {
    props:['items'],

    computed:{
        totalprice(){
            var total=0
            this.items.forEach(item => {
             total+=parseFloat(item.id)
            })

            return total
        }
    },
    methods:{
        remove(index){
            this.$emit('itemremove', index)
        }
    }

}
</script>