<script>
  import { supabase } from './conexion.js';
  import { createClient } from '@supabase/supabase-js'
  import {onMount} from 'svelte'
  import _, { where, pluck, sortBy } from 'underscore'; 
  import './lib/TailwindCSS.svelte'

 let alldata = []
 let alldataClientes = []

 //Recuperar datos de Productos
  onMount(()=>{
      getdataProductos()
  })
  async function getdataProductos(){
     await supabase
       .from('Productos')
       .select().then((res)=>{
          alldata = res.data
    }) 
  }

  onMount(()=>{
      getdataClientes()
  })
  async function getdataClientes(){
     await supabase
       .from('Clientes')
       .select().then((res)=>{
          alldataClientes = res.data
    }) 
  }
 let cliente = ''
$: clientesSort = _.sortBy(alldataClientes, 'cliente')
$: clientes = _.pluck(clientesSort, 'cliente') //listado de clientes desde la tabla Clientes

$: alldataFilter = _.where(alldata, {cliente: cliente});
</script>

<section class="text-gray-600 body-font">
  <div class="container px-5 py-24 mx-auto  flex justify-center">
    
    <div class=" lg:w-2/6 md:w-1/2 bg-gray-300 rounded-lg p-8 flex flex-col  w-full mt-10 md:mt-0">
      <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Buscar por Cliente</h2>
            <div class="relative mb-4">
            <label for="cliente" class="leading-7 text-sm text-gray-600">Cliente</label>
            <select bind:value={cliente} id="cliente" name="cliente" class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                       <option disabled selected value>Seleccione Cliente</option>
                            {#each clientes as cliente}                    
                                  <option value={cliente}>{cliente}</option>
                            {/each}                   
        </select>
      </div>
    </div>
  </div>
</section>

{#each alldataFilter as item}
    

<section class="text-gray-600 body-font overflow-hidden">
  <div class="container px-5 py-24 mx-auto">
    <div class="lg:w-4/5 mx-auto bg-gray-200 rounded-lg p-8 flex flex-wrap">
      <div class="lg:w-1/2 w-full lg:pr-10 lg:py-6 mb-6 lg:mb-0">
        <h2 class="text-sm title-font text-gray-800 text-2xl tracking-widest">{item.cliente}</h2>
        <h1 class="text-gray-900 text-3xl title-font font-medium mb-4">{item.codigo1}</h1>
        <div class="flex mb-4">
          <a class="flex-grow text-indigo-500 border-b-2 border-indigo-500 py-2 text-lg px-1">Descripción</a>
         
        </div>
        <p class="leading-relaxed mb-4">{item.descripcion}</p>

        {#if item.contenido === ''}          
        {:else}
           <div class="flex border-t border-gray-200 py-2">
          <span class="text-gray-800">Contenido</span>
          <span class="ml-auto text-gray-900">{item.contenido}</span>
        </div>
        {/if}
        
        {#if item.codigo2 === ''}

        {:else}
            <div class="flex border-t border-gray-200 py-2">
          <span class="text-gray-800">Codigo 2</span>
          <span class="ml-auto text-gray-900">{item.codigo2}</span>
        </div>
        {/if}
        
        <div class="flex border-t border-gray-200 py-2">
          <span class="text-gray-800">Largo</span>
          <span class="ml-auto text-gray-900">{item.largo}</span>
        </div>

        <div class="flex border-t border-gray-200 py-2">
          <span class="text-gray-800">Ancho</span>
          <span class="ml-auto text-gray-900">{item.ancho}</span>
        </div>
        {#if item.alto === null}           
        {:else}
          <div class="flex border-t border-gray-200 py-2">
          <span class="text-gray-800">Alto</span>
          <span class="ml-auto text-gray-900">{item.alto}</span>
        </div>
        {/if}         
        
        <div class="flex border-t border-gray-200 py-2">
          <span class="text-gray-800">Aletas Superiores</span>
          <span class="ml-auto text-gray-900">{item.aletasSuperiores}</span>
        </div>

        <div class="flex border-t border-gray-200 py-2">
          <span class="text-gray-800">Aletas Inferiores</span>
          <span class="ml-auto text-gray-900">{item.aletasInferiores}</span>
        </div>

        <div class="flex border-t border-gray-200 py-2">
          <span class="text-gray-800">Libraje</span>
          <span class="ml-auto text-gray-900">{item.libraje} lbs.</span>
        </div>

        <div class="flex border-t border-gray-200 py-2">
          <span class="text-gray-800">Liner Exterior</span>
          <span class="ml-auto text-gray-900">{item.linerExt}</span>
        </div>

        <div class="flex border-t border-gray-200 py-2">
          <span class="text-gray-800">Onda</span>
          <span class="ml-auto text-gray-900">{item.onda}</span>
        </div>

        <div class="flex border-t border-gray-200 py-2">
          <span class="text-gray-800">SKU:</span>
          <span class="ml-auto text-gray-900">{item.id}</span>
        </div>

        <div class="flex border-t border-gray-200 py-2">
          <span class="text-gray-800">Versión del diseño:</span>
          <span class="ml-auto text-gray-900">{item.version}</span>
        </div>
               
      </div>
      <img alt="planos" class="lg:w-1/2 w-full lg:h-auto h-64 object-contain object-center rounded" src={item.fotoPlano}>
    </div>
  </div>
  <hr/>
</section>
{/each}