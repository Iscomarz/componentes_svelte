<script>

    import {onMount, onDestroy, beforeUpdate, afterUpdate, tick} from 'svelte'

    export let nombre

    let mostrar;

    function entrar(){
        mostrar = true
    }

    function salir(){
        mostrar = false
    }

    //creacion
    //script
    console.log("Se ejecuta primero")
    //onMount
    onMount(async ()=>{
        console.log("Se ejecuta tercer lugar")
        await tick()
        console.log("Se ejecuta cuando todos los metedos ya se ejecutaron")
    })
    //onDestroy
    onDestroy(()=>{
        console.log("Se ejecuta cuando se elimnia el componente")
    })
    //actualizacion del DOM
    beforeUpdate(()=>{
        console.log("Se ejecuta antes de actualizar el dom")
    })
    //afterUpdate
    afterUpdate(()=>{
        console.log("Se ejecuta despues de actualizar el dom")
    })
    //tick

</script>

<style>
    h2{
        color: red;
        font-weight: bolder;
        text-decoration: underline;
    }
</style>

<div class="jumbotrone mt-4" on:mouseenter={entrar} on:mouseleave={salir}>
    <h1>{nombre}</h1>
    <h2>
        <slot name="subtitulo">
            <span>Agregar subtitulo aqui</span>
        </slot>
    </h2>
    <slot mostrar={mostrar}></slot>
</div>