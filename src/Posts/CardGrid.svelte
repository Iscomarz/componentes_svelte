<script>
    import Card from "./Card.svelte";
    export let post;

    function verMas(){
        alert('Informacion')
    }

    function favorito(){
        alert('favorito')
    }
</script>

<div class="grid grid-cols-3 gap-2">
    {#each post as item}
    <div>
        <Card 
        titulo={item.titulo} 
        descripcion={item.descripcion} 
        imagen={item.imagen}
        on:ver-mas={verMas}
        on:favorito={favorito}/>
    </div>
        
    {/each}
</div>