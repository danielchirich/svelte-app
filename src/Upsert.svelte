<script>
  import { supabase } from './conexion.js';
  import { createClient } from '@supabase/supabase-js'
  import {onMount} from 'svelte'
  import _, { pluck } from 'underscore'; 
  import  { sortBy } from 'underscore'; 
  
  import './lib/TailwindCSS.svelte'
  
  let alldata
  let alldataClientes = []
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
  let codigo1 = ''
  let codigo2 = ''
  let contenido = ''
  let largo = ''
  let ancho = ''
  let alto = ''
  let largoTroquelar = ''
  let anchoTroquelar = ''
  let aletasSuperiores = ''
  let aletasInferiores = ''
  let impresionColores = ''
  let libraje = ''
  let linerExt = ''
  let onda = ''
  let fotoPlano = ''
  let descripcion = ''
  let fecha = ''
  let version = '' 
  
async function upsertCliente(id,
                               cliente,
                                codigo1,
                                 codigo2,
                                  contenido,
                                   largo,
                                    ancho,
                                     alto,
                                     largoTroquelar,
                                      anchoTroquelar,
                                       aletasSuperiores,
                                        aletasInferiores,
                                         impresionColores,
                                          libraje,
                                           linerExt,
                                            onda,
                                             fotoPlano,
                                              descripcion,
                                               version) {
  
    await supabase
    .from('Productos')
    .upsert({ id: id,
              cliente: cliente,
              codigo1: codigo1,
              codigo2: codigo2,
              contenido: contenido,
              largo: largo,
              ancho: ancho,
              alto: alto,
              largoTroquelar: largoTroquelar,
              anchoTroquelar: anchoTroquelar,
              aletasSuperiores: aletasSuperiores,
              aletasInferiores: aletasInferiores,
              impresionColores: impresionColores,
              libraje: libraje,
              linerExt: linerExt,
              onda: onda,
              fotoPlano: fotoPlano,
              descripcion: descripcion,                                           
              version: version                        
                        })}

let versiones = ["1", "2", "3", "4"]
let librajes = [70, 80, 90, 100, 110, 120, 130, 150, 170, 200, 220, 250]
$: clientesSort = _.sortBy(alldataClientes, 'cliente')
$: clientes = _.pluck(clientesSort, 'cliente')
 

</script>

<section class="text-gray-600 body-font">
  <div class="container px-5 py-24 mx-auto  flex justify-center">
    
    <div class=" lg:w-2/6 md:w-1/2 bg-gray-400 rounded-lg p-8 flex flex-col  w-full mt-10 md:mt-0">
      <h2 class="text-gray-900 text-lg text-red-700 font-medium title-font mb-5">Upsert Productos</h2>

      <div class="relative mb-4">
        <label for="id" class="leading-7 text-sm text-gray-600">id</label>
        <input bind:value={id} type=number id="id" name="id" placeholder='Enter id...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
      </div>

      

      <div class="relative mb-4">
        <label for="cliente" class="leading-7 text-sm text-gray-600">Cliente</label>
        <select bind:value={cliente} id="cliente" name="cliente" class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                       <option disabled selected value>Seleccione Cliente</option>
                            {#each clientes as cliente}                    
                                  <option value={cliente}>{cliente}</option>
                            {/each}                   
        </select>
      </div>
      <div class="relative mb-4">
        <label for="codigo1" class="leading-7 text-sm text-gray-600">Codigo 1</label>
        <input bind:value={codigo1} id="codigo1" name="codigo1" placeholder='Enter Codigo...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
      </div>

      <div class="relative mb-4">
        <label for="codigo2" class="leading-7 text-sm text-gray-600">Codigo 2</label>
        <input bind:value={codigo2} id="codigo2" name="codigo2" placeholder='Enter Codigo...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
      </div>

      <div class="relative mb-4">
        <label for="contenido" class="leading-7 text-sm text-gray-600">Contenido</label>
        <input bind:value={contenido}  id="contenido" name="contenido" placeholder='Enter Contenido...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
      </div>

      <div class="relative mb-4">
        <label for="largo" class="leading-7 text-sm text-gray-600">Largo</label>
        <input bind:value={largo} type=number id="largo" name="largo" placeholder='Enter Largo...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
      </div>

      <div class="relative mb-4">
        <label for="ancho" class="leading-7 text-sm text-gray-600">Ancho</label>
        <input bind:value={ancho} type=number id="ancho" name="ancho" placeholder='Enter Ancho...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
      </div>

      <div class="relative mb-4">
        <label for="alto" class="leading-7 text-sm text-gray-600">Alto</label>
        <input bind:value={alto} type=number id="alto" name="alto" placeholder='Enter Alto...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
      </div>

      <div class="relative mb-4">
        <label for="largoTroquelar" class="leading-7 text-sm text-gray-600">Largo para Troquelar</label>
        <input bind:value={largoTroquelar} type=number id="largoTroquelar" name="largoTroquelar" placeholder='Enter Largo para Troquelar...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
      </div>

      <div class="relative mb-4">
        <label for="anchoTroquelar" class="leading-7 text-sm text-gray-600">Ancho para Troquelar</label>
        <input bind:value={anchoTroquelar} type=number id="anchoTroquelar" name="anchoTroquelar" placeholder='Enter Largo para Troquelar...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
      </div>

      <div class="relative mb-4">
        <label for="aletasSup" class="leading-7 text-sm text-gray-600">Aletas Superiores</label>
        <select bind:value={aletasSuperiores} id="aletasSup" name="aletasSup"  class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                          <option disabled selected value>Seleccione Tipo Aletas</option>
                          <option value='Simples'>Simples</option>
                          <option value='Dobles'>Dobles</option>
                          <option value='Encimadas'>Encimadas</option>
                          <option value='sin Aletas'>sin Aletas</option>         
        </select>
      </div>

      <div class="relative mb-4">
        <label for="aletasInf" class="leading-7 text-sm text-gray-600">Aletas Inferiores</label>
        <select bind:value={aletasInferiores} id="aletasInf" name="aletasInf"  class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                   <option disabled selected value>Seleccione Tipo Aletas</option>
                    <option value='Simples'>Simples</option>
                    <option value='Dobles'>Dobles</option>
                    <option value='Encimadas'>Encimadas</option>
                    <option value='sin Aletas'>sin Aletas</option>         
        </select>
      </div>

      <div class="relative mb-4">
        <label for="impresionColores" class="leading-7 text-sm text-gray-600">Impresión</label>
        <input bind:value={impresionColores} id="impresionColores" name="impresionColores" placeholder='Enter Colores de Impresión...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
      </div>

      <div class="relative mb-4">
        <label for="libraje" class="leading-7 text-sm text-gray-600">libraje</label>
        <select bind:value={libraje} type=number id="libraje" name="libraje" class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                       <option disabled selected value>Seleccione Libraje</option>
                            {#each librajes as libraje}                    
                                  <option value={libraje}>{libraje}</option>
                            {/each}                   
        </select>
      </div>

      <div class="relative mb-4">
        <label for="linerExt" class="leading-7 text-sm text-gray-600">Liner Exterior</label>
        <select bind:value={linerExt} id="linerExt" name="linerExt" placeholder='Enter liner exterior...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                     <option disabled selected value>Seleccione Color liner</option>
                     <option value='Kraft'>Kraft</option>
                     <option value='Blanco'>Blanco</option>
        </select>
      </div>

      <div class="relative mb-4">
        <label for="onda" class="leading-7 text-sm text-gray-600">Onda</label>
        <select bind:value={onda} id="onda" name="onda" class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                     <option disabled selected value>Seleccione Tipo de Onda</option>
                     <option value='Simple'>Simple</option>
                     <option value='Doble/Triple'>Doble/Triple</option>
        </select>
      </div>

      <div class="relative mb-4">
        <label for="fotoPlano" class="leading-7 text-sm text-gray-600">Plano</label>
        <input bind:value={fotoPlano} id="fotoPlano" name="fotoPlano" placeholder='Enter dirección foto...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
      </div>

      
      <div class="relative mb-4">
        <label for="descripcion" class="leading-7 text-sm text-gray-600">Descripción</label>
        <textarea bind:value={descripcion} id="descripcion" name="descripcion" placeholder='Enter descripción, notas...' class="w-full bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-white focus:ring-2 focus:ring-indigo-200 h-32 text-base outline-none text-gray-700 py-1 px-3 resize-none leading-6 transition-colors duration-200 ease-in-out"></textarea>
      </div>

      <div class="relative mb-4">
        <label for="version" class="leading-7 text-sm text-gray-600">version</label>
        <select bind:value={version}   id="version" name="version" placeholder='Enter version del diseño...' class="w-full bg-white rounded border border-gray-300 focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">
                     <option disabled selected value>Seleccione Versión Producto</option>
              {#each versiones as version}                    
                    <option value={version}>{version}</option>
              {/each}        
                   
                  
        </select>
      </div>
    
      <br/>
      
       <button on:click={upsertCliente(id, cliente, codigo1, codigo2, contenido, alto, ancho, alto, largoTroquelar, anchoTroquelar, aletasSuperiores, aletasInferiores, impresionColores, libraje, linerExt, onda, fotoPlano, descripcion, version)} class="text-white bg-red-500 border-0 py-2 px-8 focus:outline-none hover:bg-red-600 rounded text-lg">Upsert
       
       </button>    
     
      <p class="text-xs text-gray-500 mt-3">No pude aguantar tus ojos. Mirabas de frente, como los chicos, y decías las cosas del mismo modo. Eso era. Abelardo Castillo </p>
    </div>
  </div>
</section>
