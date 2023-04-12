<template>
    <div>
        <div>
            <label for="">Filtrar por edad: </label>
            <input type="text" v-model="search">
        </div>
        <ul>
            <template v-for="item in searchFn" v-bind:key="item.id">
                <li>{{ item.name }} - {{ item.year }}</li>
            </template>
        </ul>
    </div>
</template>

<script>
import { ref, computed } from 'vue';
export default {
    name: 'List',
    props: {
    },
    setup() {
        let search = ref('');
        let obj = [
            {
                id: 1,
                name: "Carlos",
                year: 35
            },
            {
                id: 2,
                name: "Lus Maria",
                year: 24
            },
            {
                id: 3,
                name: "Susana",
                year: 30
            }
        ];

        const searchFn = computed(() => {
            if(search.value!=""){
                return obj.filter(user => user.year==search.value );
                // return obj.filter(usr => {
                //     usr.year <= search.value;
                // });
            }else{
                return obj;
            }
        })

        return {
            obj,
            search,
            searchFn
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
