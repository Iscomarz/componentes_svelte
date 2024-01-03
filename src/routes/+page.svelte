<script>
    import InputCustom from "../desing/inputCustom.svelte";
    import Header from "../lib/Header.svelte";
    import CardGrid from "../Posts/CardGrid.svelte";
    import JumboTrone from "../desing/jumboTrone.svelte";

    let titulo= ''
    let descripcion = ''
    let imagen = ''
    let show = false;

    let post = [
        {
          id:'1',
          titulo: 'Trabajando con svelte',
          descripcion: 'Descripcion del post con svelte',
          imagen: 'https://images.pexels.com/photos/19582452/pexels-photo-19582452/free-photo-of-libros-biblioteca-educacion-conocimiento.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1'
        },
        {
          id:'2',
          titulo: 'Trabajando con svelte 2',
          descripcion: 'Descripcion del post con svelte',
          imagen: 'https://images.pexels.com/photos/1050585/pexels-photo-1050585.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1'
        },
        {
          id:'3',
          titulo: 'Trabajando con svelte 3',
          descripcion: 'Descripcion del post con svelte',
          imagen: 'https://images.pexels.com/photos/17902478/pexels-photo-17902478/free-photo-of-comida-amanecer-cafeina-cafe.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1'
        }     
    ]

    function agregarPost(){
      const nuevopost = {
        id: Math.random().toString(),
        titulo: titulo,
        descripcion: descripcion,
        imagen: imagen
      }

      post = [nuevopost, ...post]
    }
</script>

<Header color="gray" titulo="Navbar" logo="CODE"/>

<div class="container">

Mostrar jumbotron <input type="checkbox" bind:checked={show}>

{#if show}
<JumboTrone nombre="Mis componentes" let:mostrar={mostrar}>
  <span slot="subtitulo">Nuevo subtitulo</span>
  <div class:mostrar>
    {#if mostrar}
      <hr>
      <button>Boton</button>
      {:else}
      <h2>Coloca el mouse arriba</h2>
    {/if}
  </div>
</JumboTrone>
{/if}

<CardGrid {post} />

<form on:submit|preventDefault={agregarPost}>
  
    <InputCustom type="text" nombre="Titulo" id="titulo" placeholder="Titulo" value={titulo} on:input={event => (titulo = event.target.value)}/>
    <InputCustom type="text" nombre="Imagen" id="imagen" placeholder="Imagen" value={imagen} on:input={event => (imagen = event.target.value)}/>
    <InputCustom control="textarea" nombre="Descripcion" id="descripcion" placeholder="Descripcion" value={descripcion} on:input={event => (descripcion = event.target.value)}/>
    <button type="submit" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-1/4 px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800 mt-2">Guardar</button> 
</form>

</div>

<h1 class="text-3xl font-bold underline">
    Welcome to SvelteKit
</h1>
<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>

<style lang="postcss">
    :global(html) {
      background-color: theme(colors.gray.100);
    }
  </style>