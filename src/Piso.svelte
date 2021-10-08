<script>
    import { supabase } from './conexion.js';
    import { createClient } from '@supabase/supabase-js';
    import {onMount} from 'svelte';
    import _, { pluck } from 'underscore'; 
    import  { sortBy } from 'underscore'; 
    import './lib/TailwindCSS.svelte';
    
  
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
    //Recuperar datos de Clientes
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
     //Cargar Datos
    let id = ''
    let cliente = ''
    let codigo1= ''
    let codigo2= ''
    let contenido= ''
    let largo = ''
    let ancho = ''       
    let impresionColores= ''
    let libraje= ''
    let linerExt= ''
    let onda= ''
    let fotoPlano= ''
    let descripcion= ''
    let fecha = '' 
    let version = ''
    
  
    let datanueva = [
          { cliente: '',
            codigo1: '',
            codigo2: '',
            contenido: '',
            largo: '',
            ancho: '',
                   
            impresionColores: '',
            libraje: '',
            linerExt: '',
            onda: '',
            fotoPlano: '',
            descripcion: '',          
            version: ''
              }
          ]  
    async function cargarDatos() {  
      await supabase
      .from('Productos')
      .insert(datanueva)
      datanueva = [...datanueva, alldata]
      datanueva = [
          { cliente: '',
            codigo1: '',
            codigo2: '',
            contenido: '',
            largo: '',
            ancho: '',
                 
            impresionColores: '',
            libraje: '',
            linerExt: '',
            onda: '',
            fotoPlano: '',
            descripcion: '',          
            version: ''
              }]  
    }
    
   let versiones = ["1", "2", "3", "4"]
   let librajes = [70, 80, 90, 100, 110, 120, 130, 150, 170, 200, 220, 250]
   $: clientesSort = _.sortBy(alldataClientes, 'cliente')
   $: clientes = _.pluck(clientesSort, 'cliente')
  
  
   
  </script>
  
  <section class="text-gray-600 body-font">
    <div class="container px-5 py-24 mx-auto  flex justify-center">
      
      <div class=" lg:w-2/6 md:w-1/2 bg-gray-300 rounded-lg p-8 flex flex-col  w-full mt-10 md:mt-0">
        <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Pisos</h2>
      {#each datanueva as item}
         
      
        <div class="relative mb-4">
          <label for="cliente" class="leading-7 text-sm text-gray-600">Cliente</label>
          <select bind:value={item.cliente} id="cliente" name="cliente" class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                         <option disabled selected value>Seleccione Cliente</option>
                              {#each clientes as cliente}                    
                                    <option value={cliente}>{cliente}</option>
                              {/each}                   
          </select>
        </div>
        <div class="relative mb-4">
          <label for="codigo1" class="leading-7 text-sm text-gray-600">Codigo 1</label>
          <input bind:value={item.codigo1} id="codigo1" name="codigo1" placeholder='Enter Codigo...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
        </div>
  
        <div class="relative mb-4">
          <label for="codigo2" class="leading-7 text-sm text-gray-600">Codigo 2</label>
          <input bind:value={item.codigo2} id="codigo2" name="codigo2" placeholder='Enter Codigo...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
        </div>
  
        <div class="relative mb-4">
          <label for="contenido" class="leading-7 text-sm text-gray-600">Contenido</label>
          <input bind:value={item.contenido}  id="contenido" name="contenido" placeholder='Enter Contenido...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
        </div>
  
        <div class="relative mb-4">
          <label for="largo" class="leading-7 text-sm text-gray-600">Largo</label>
          <input bind:value={item.largo} type=number id="largo" name="largo" placeholder='Enter Largo...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
        </div>
  
        <div class="relative mb-4">
          <label for="ancho" class="leading-7 text-sm text-gray-600">Ancho</label>
          <input bind:value={item.ancho} type=number id="ancho" name="ancho" placeholder='Enter Ancho...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
        </div>

         
        
        
        <div class="relative mb-4">
          <label for="impresionColores" class="leading-7 text-sm text-gray-600">Impresión</label>
          <input bind:value={item.impresionColores} id="impresionColores" name="impresionColores" placeholder='Enter Colores de Impresión...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
        </div>
  
        <div class="relative mb-4">
          <label for="libraje" class="leading-7 text-sm text-gray-600">libraje</label>
          <select bind:value={item.libraje} type=number id="libraje" name="libraje" class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                         <option disabled selected value>Seleccione Libraje</option>
                              {#each librajes as libraje}                    
                                    <option value={libraje}>{libraje}</option>
                              {/each}                   
          </select>
        </div>
  
        <div class="relative mb-4">
          <label for="linerExt" class="leading-7 text-sm text-gray-600">Liner Exterior</label>
          <select bind:value={item.linerExt} id="linerExt" name="linerExt" placeholder='Enter liner exterior...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                       <option disabled selected value>Seleccione Color liner</option>
                       <option value='Kraft'>Kraft</option>
                       <option value='Blanco'>Blanco</option>
          </select>
        </div>
  
        <div class="relative mb-4">
          <label for="onda" class="leading-7 text-sm text-gray-600">Onda</label>
          <select bind:value={item.onda} id="onda" name="onda" class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                       <option disabled selected value>Seleccione Tipo de Onda</option>
                       <option value='Simple'>Simple</option>
                       <option value='Doble/Triple'>Doble/Triple</option>
          </select>
        </div>
  
        <div class="relative mb-4">
          <label for="fotoPlano" class="leading-7 text-sm text-gray-600">Plano</label>
          <input bind:value={item.fotoPlano} id="fotoPlano" name="fotoPlano" placeholder='Enter dirección foto...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
        </div>
  
        
        <div class="relative mb-4">
          <label for="descripcion" class="leading-7 text-sm text-gray-600">Descripción</label>
          <textarea bind:value={item.descripcion} id="descripcion" name="descripcion" placeholder='Enter descripción, notas...' class="w-full bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-white focus:ring-2 focus:ring-indigo-200 h-32 text-base outline-none text-gray-700 py-1 px-3 resize-none leading-6 transition-colors duration-200 ease-in-out"></textarea>
        </div>
  
        <div class="relative mb-4">
          <label for="version" class="leading-7 text-sm text-gray-600">version</label>
          <select bind:value={item.version}   id="version" name="version" placeholder='Enter version del diseño...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                       <option disabled selected value>Seleccione Versión Producto</option>
                {#each versiones as version}                    
                      <option value={version}>{version}</option>
                {/each}        
                     
                    
          </select>
        </div>
  
      {/each}
        <button on:click={() => cargarDatos()} class="text-white bg-indigo-500 border-0 py-2 px-8 focus:outline-none hover:bg-indigo-600 rounded text-lg">Ingresar Datos</button>
        <br/>
          
       
        <p class="text-xs text-gray-500 mt-3">Estaba atorado. Imaginé mi forma de pensar como círculos progresivos y concéntricos que a veces se amplían y otras se contraen hasta ser un punto: Olga</p>
      </div>
    </div>
  </section>
  
  
  
