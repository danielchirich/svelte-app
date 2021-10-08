<script>
  import Header from './Header.svelte';
  import Troquelado from './Troquelado.svelte';
  import Bandeja from './Bandeja.svelte';
  import Footer from './Footer.svelte';
  import Clientes from './Clientes.svelte';
  import Standart from './Standart.svelte';
  // @ts-ignore
  import Producto from './Producto.svelte'; 
  import Delete from "./Delete.svelte"; 
  import Upsert from './Upsert.svelte'; 
  import Piso from './Piso.svelte';

  
  import './lib/TailwindCSS.svelte'
 
  let opcion1 = false
  let opcion2 = false
  let opcion3 = false
  let opcion4 = false
  let opcion5 = false
  let opcion6 = false
  let opcion7 = false
  let opcion8 = false
  
</script>
<Header />
<!-- Toggle B -->
<main>
<section class="text-gray-600 body-font">
<!-- Toggle B <div class="bg-gray-400 text-gray-600 px-4 py-4 rounded relative text-sm text-center">
 --> 
<div class="container px-0 py-0 mx-auto flex justify-center items-center">
   <div class=" lg:w-2/6 md:w-1/2 bg-gray-400 flex justify-between   p-8  flex-col  w-full mt-0 md:mt-0 ">
      <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Ver Productos por cliente</h2>
       <div class="flex  justify-between items-center w-full mb-12">
  
            <label for="toggleB1" class="flex items-start cursor-pointer">
                  <!-- toggle -->
                  <div class="relative">
                   <!-- input -->
                  <input type="checkbox" id="toggleB1" class="sr-only" bind:checked={opcion1}>
                  <!-- line -->
                  <div class="block bg-gray-600 w-14 h-8 rounded-full"></div>
                  <!-- dot -->
                  <div class="dot absolute left-1 top-1 bg-white w-6 h-6 rounded-full transition"></div>
                  </div>
                   <!-- label -->
                  <div class="ml-3 text-gray-700 font-medium">
                  Productos
                   </div>
           </label>
      </div>
    <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Cargar datos para Cajas Standart</h2> 
     <div class="flex items-start justify-item-end w-full mb-12">
  
            <label for="toggleB2" class="flex items-center cursor-pointer">
                  <!-- toggle -->
                  <div class="relative">
                   <!-- input -->
                  <input type="checkbox" id="toggleB2" class="sr-only" bind:checked={opcion2}>
                  <!-- line -->
                  <div class="block bg-gray-600 w-14 h-8 rounded-full"></div>
                  <!-- dot -->
                  <div class="dot absolute left-1 top-1 bg-white w-6 h-6 rounded-full transition"></div>
                  </div>
                   <!-- label -->
                  <div class="ml-3 text-gray-700 font-medium">
                  Standart
                   </div>
           </label>
      </div>

      <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Delete Productos</h2> 
     <div class="flex items-start justify-item-end w-full mb-12">
  
            <label for="toggleB3" class="flex items-center cursor-pointer">
                  <!-- toggle -->
                  <div class="relative">
                   <!-- input -->
                  <input type="checkbox" id="toggleB3" class="sr-only" bind:checked={opcion3}>
                  <!-- line -->
                  <div class="block bg-gray-600 w-14 h-8 rounded-full"></div>
                  <!-- dot -->
                  <div class="dot absolute left-1 top-1 bg-white w-6 h-6 rounded-full transition"></div>
                  </div>
                   <!-- label -->
                  <div class="ml-3 text-gray-700 font-medium">
                  Delete
                   </div>
           </label>
      </div>

      <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Upsert Productos</h2> 
     <div class="flex items-start justify-item-end w-full mb-12">
  
            <label for="toggleB4" class="flex items-center cursor-pointer">
                  <!-- toggle -->
                  <div class="relative">
                   <!-- input -->
                  <input type="checkbox" id="toggleB4" class="sr-only" bind:checked={opcion4}>
                  <!-- line -->
                  <div class="block bg-gray-600 w-14 h-8 rounded-full"></div>
                  <!-- dot -->
                  <div class="dot absolute left-1 top-1 bg-white w-6 h-6 rounded-full transition"></div>
                  </div>
                   <!-- label -->
                  <div class="ml-3 text-gray-700 font-medium">
                  Upsert
                   </div>
           </label>
      </div>

      <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Nuevo Cliente</h2> 
     <div class="flex items-start justify-item-end w-full mb-12">
  
            <label for="toggleB5" class="flex items-center cursor-pointer">
                  <!-- toggle -->
                  <div class="relative">
                   <!-- input -->
                  <input type="checkbox" id="toggleB5" class="sr-only" bind:checked={opcion5}>
                  <!-- line -->
                  <div class="block bg-gray-600 w-14 h-8 rounded-full"></div>
                  <!-- dot -->
                  <div class="dot absolute left-1 top-1 bg-white w-6 h-6 rounded-full transition"></div>
                  </div>
                   <!-- label -->
                  <div class="ml-3 text-gray-700 font-medium">
                  Cliente
                   </div>
           </label>
      </div>

        <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Cargar datos para Troquelado</h2> 
           <div class="flex items-start justify-item-end w-full mb-12">
  
            <label for="toggleB6" class="flex items-center cursor-pointer">
                  <!-- toggle -->
                  <div class="relative">
                   <!-- input -->
                  <input type="checkbox" id="toggleB6" class="sr-only" bind:checked={opcion6}>
                  <!-- line -->
                  <div class="block bg-gray-600 w-14 h-8 rounded-full"></div>
                  <!-- dot -->
                  <div class="dot absolute left-1 top-1 bg-white w-6 h-6 rounded-full transition"></div>
                  </div>
                   <!-- label -->
                  <div class="ml-3 text-gray-700 font-medium">
                  Troquelado
                   </div>
           </label>
        </div>

        <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Cargar datos para Bandeja</h2> 
           <div class="flex items-start justify-item-end w-full mb-12">
  
            <label for="toggleB7" class="flex items-center cursor-pointer">
                  <!-- toggle -->
                  <div class="relative">
                   <!-- input -->
                  <input type="checkbox" id="toggleB7" class="sr-only" bind:checked={opcion7}>
                  <!-- line -->
                  <div class="block bg-gray-600 w-14 h-8 rounded-full"></div>
                  <!-- dot -->
                  <div class="dot absolute left-1 top-1 bg-white w-6 h-6 rounded-full transition"></div>
                  </div>
                   <!-- label -->
                  <div class="ml-3 text-gray-700 font-medium">
                  Bandeja
                   </div>
           </label>
        </div>

        <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Cargar datos para Piso</h2> 
           <div class="flex items-start justify-item-end w-full mb-12">
  
            <label for="toggleB8" class="flex items-center cursor-pointer">
                  <!-- toggle -->
                  <div class="relative">
                   <!-- input -->
                  <input type="checkbox" id="toggleB8" class="sr-only" bind:checked={opcion8}>
                  <!-- line -->
                  <div class="block bg-gray-600 w-14 h-8 rounded-full"></div>
                  <!-- dot -->
                  <div class="dot absolute left-1 top-1 bg-white w-6 h-6 rounded-full transition"></div>
                  </div>
                   <!-- label -->
                  <div class="ml-3 text-gray-700 font-medium">
                  Piso
                   </div>
           </label>
        </div>
  </div>
</div>
</section> 
{#if opcion1}
          <Producto/>
{/if}

{#if opcion2}
          <Standart/>
{/if}

{#if opcion3}
          <Delete/>
{/if}

{#if opcion4}
          <Upsert/>
{/if}

{#if opcion5}
          <Clientes/>
{/if}

{#if opcion6}
          <Troquelado/>
{/if}

{#if opcion7}
          <Bandeja/>
{/if}
{#if opcion8}
          <Piso/>
{/if}
</main>

<Footer/>

<style>
input:checked ~ .dot {
  transform: translateX(100%);
  background-color: #48bb78;
}
/* Toggle B */
input:checked ~ .dot {
  transform: translateX(100%);
  background-color: #48bb78;
}
main {
  background-color: rgba(156, 163, 175);
}
</style>
