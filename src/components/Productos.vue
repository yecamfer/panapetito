<template>
    <div class="contedor">
        <Titulo :titulo="props.categoria" />
        <div class="productos">
            <div class="producto" v-for="producto in productos" :key="producto.id">
                <img class="foto" src="`/imagenes/${producto.imagen}`" alt="Producto">
                <div class="informacion">
                    <h3 class="titulo">
                        {{ producto.nombre }}
                    </h3>
                    <p class="descrpicion">
                        {{ producto.descrpicion }}
                    </p>
                    <p class="precio">
                        ${{ producto.precio }}
                    </p>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import {ref, defineProps ,watchEffect} from "vue"
import Titulo from "@/componets/TituloSeccion.vue"
import listaProductos from "@/panaderia.json"


const props=defineProps({
    categoria:String
})

const productos =ref([])

watchEffect(() => {
    producto.value = listaProductos.filter((producto) => producto.categoria ===props.categoria)
})
</script>