<script>
  import { supabase } from './conexion.js';
  import { createClient } from '@supabase/supabase-js'
  import {onMount} from 'svelte'
  import './lib/TailwindCSS.svelte'


  let data = []
  let cliente = ''

 onMount(()=>{
      getdataClientes()
  })
  async function getdataClientes(){
     await supabase
       .from('Clientes')
       .select().then((res)=>{
          data = res.data
    }) 
  }
 
  async function insertCliente(cliente) {
    try {
       const { data, error } = await supabase
         .from('Clientes')
         .insert([
                   { cliente: cliente }
         ])
        
    } catch (error) {
      console.log(error)
    }
  } 
  let id 
  async function deleteCliente(id) {
    try {
      const { data, error } = await supabase
      .from('Clientes')
      .delete()
      .match({ id: id })
    } catch (error) {
    console.log(error)
    }
    
  }





</script>

<section class="text-gray-600 body-font">
  <div class="container px-5 py-6 mx-auto  flex justify-center">
    
    <div class=" lg:w-2/6 md:w-1/2 bg-gray-300 rounded-lg p-8 flex flex-col  w-full mt-10 md:mt-0">
      <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Nuevo Cliente</h2>
        <div class="relative mb-4">
        <label for="Cliente" class="leading-7 text-sm text-gray-600">Cliente</label>
        <input bind:value={cliente} id="cliente" name="cliente" placeholder='Enter Cliente...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
        </div>
        <button on:click={() => insertCliente(cliente)} class="text-white bg-indigo-500 border-0 py-2 px-8 focus:outline-none hover:bg-indigo-600 rounded text-lg">Ingresar Nuevo Cliente</button>
        <p class="text-xs text-gray-500 mt-3">No pude aguantar tus ojos. Mirabas de frente, como los chicos, y decías las cosas del mismo modo. Eso era. Abelardo Castillo </p>
         
    </div>    
  </div>
  
</section>  

<section class="text-gray-600 body-font">
  <div class="container px-5 py-6 mx-auto  flex justify-center">
    <div class=" lg:w-2/6 md:w-1/2 bg-gray-300 rounded-lg p-8 flex flex-col  w-full mt-10 md:mt-0">
      <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Clientes</h2>
         {#each data as item}
            <ul>
                <li>id: {item.id} - {item.cliente} </li>
           </ul>
         {/each}      
    </div>
  </div>
</section>

 <div class="container px-5 py-6 mx-auto  flex justify-center">
    <div class=" lg:w-2/6 md:w-1/2 bg-gray-400 rounded-lg p-8 flex flex-col  w-full mt-10 md:mt-0">
      <h2 class="text-gray-900 text-lg text-red-700 font-medium title-font mb-5">Delete Clientes</h2>
    
      
      <div class="relative mb-4">
       <input bind:value={id} id="id" name="id" placeholder='id' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
       </div>
       <button on:click|preventDefault={deleteCliente(id)} class="text-white bg-red-500 border-0 py-2 px-8 focus:outline-none hover:bg-red-600 rounded text-lg">Borrar Cliente       
       </button>    
     
      <p class="text-xs text-gray-500 mt-3">Después nos quedamos quietos, como dos muertos. Y ella acercó su mano a la mía. Entonces hice algo que quizá estaba pensando hacer desde hacía tres años: retiré la mano. Abelardo Castillo </p>
    </div>
  </div>  
 
