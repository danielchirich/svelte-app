<script>
  import { supabase } from './conexion.js';
  import { createClient } from '@supabase/supabase-js'
  import {onMount} from 'svelte'
  
  import './lib/TailwindCSS.svelte'
  

   let alldata = []
   

 
  //Recuperar datos de Clientes
  onMount(()=>{
      getdata()
  })
  async function getdata(){
     await supabase
       .from('Productos')
       .select().then((res)=>{
          alldata = res.data
    }) 
  }
let id = ''


 async function deleteDatos(id) {  
    await supabase
    .from('Productos')
    .delete().match({ id: id })
     
    }
 
</script>

<section class="text-gray-600 body-font">
  <div class="container px-5 py-24 mx-auto  flex justify-center">
    
    <div class=" lg:w-2/6 md:w-1/2 bg-gray-400 rounded-lg p-8 flex flex-col  w-full mt-10 md:mt-0">
      <h2 class="text-gray-900 text-lg text-red-700 font-medium title-font mb-5">Delete Productos</h2>
    
      <br/>
      <div class="relative mb-4">
       <input bind:value={id} id="id" name="id" placeholder='id' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
       </div>
       <button on:click|preventDefault={deleteDatos(id)} class="text-white bg-red-500 border-0 py-2 px-8 focus:outline-none hover:bg-red-600 rounded text-lg">Borrar Datos
       
       </button>    
     
      <p class="text-xs text-gray-500 mt-3">No pude aguantar tus ojos. Mirabas de frente, como los chicos, y decías las cosas del mismo modo. Eso era. Abelardo Castillo </p>
    </div>
  </div>
</section>

