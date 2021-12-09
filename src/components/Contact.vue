<template>
    <div>
         <div class="flex flex-col h-screen text-sm text-gray-400">
            <div class=" flex-1 flex">
                <!-- form -->
                <div class="sidebar w-1/3 flex-none flex flex-col justify-between">
                    <form class="ml-2 my-10 px-20" @submit.prevent="addContact">
                        <div class="">
                            <input v-model="name" required class="shadow appearance-none border rounded w-full py-2 mb-3 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" type="text" placeholder="name">
                            <input v-model="number" required class="shadow appearance-none border rounded w-full py-2 mb-3 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" type="text" placeholder="phone number">
                            <input v-model="email" required class="shadow appearance-none border rounded w-full py-2 mb-3 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" type="text" placeholder="email">
                        </div>
                        <div class="">
                            <button  class="bg-blue-800 py-2 px-2 text-white hover:bg-blue-500 rounded font-bold" type="submit">Adicionar Contacto</button>
                        </div>
                    </form>
                </div>
                <!-- !form -->

                <!-- list of contacts -->
                
                <div class="content flex-1 w-2/3 flex flex-col">
                        <div class="items-center mt-4 ">
                                <div v-for="(contact,index) in contacts" :key="index" class="shadow-md bg-white w-auto inline-block px-4 py-4 mx-3 my-4">
                                        <p class="text-lg text-blue-600 text-justify font-serif border-b-2 pb-2">{{contact.name}}</p>
                                        <h3 class="text-lg text-blue-700 pt-2">{{contact.number}}</h3>
                                        <h3 class="text-lg text-blue-700 pt-2">{{contact.email}}</h3>
                                    <button  class="bg-red-800 py-2 px-2 text-white hover:bg-red-500 rounded" @click="deleteContact(index)" type="button"> Eliminar </button>
                                    <button  class="bg-yellow-600 py-2 px-2 text-white hover:bg-yellow-500 rounded"  type="button"> Editar </button>
                                    <button  class="bg-green-800 py-2 px-2 text-white hover:bg-green-500 rounded"  type="button"> Ver Contacto </button>
                                </div>                  
                        </div>
                </div>
                
                <!-- !list of contacts -->
                
            </div>
        </div>
    </div>
    
</template>

<script>
export default {
    data(){
        return{
            name:'',
            number:'',
            email:'',
            contacts:[]
        }
    },
    methods:{
        addContact(){
            const contact={
                name:this.name,
                number:this.number,
                email:this.email
            };
            this.contacts.push(contact)
            console.log(this.contacts);
        },
        deleteContact(index){
            this.$delete(this.contacts,index);
        }
    },
}
</script>
