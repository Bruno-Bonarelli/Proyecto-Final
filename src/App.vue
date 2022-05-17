<template>
    <div id="app">
        <CarritoDeCompras :productos="productosEnCarrito" />

        <div class="contenedorProductos">
            <ProductoVenta
                attr1="attr1"
                attr2="attr2"
                v-bind="$attrs"
                v-for="(item, i) in productos"
                :key="i"
                :id="item.id"
                :titulo="item.titulo"
                :precio="item.precio"
                :nombre-imagen="item.nombreImagen"
                :destacado="item.destacado"
                @agregar-al-carrito="AgregarAlCarrito"
            >
            </ProductoVenta>
        </div>

        
    </div>
</template>


<script>
import ProductoVenta from "./components/Productos-venta.vue";
import CarritoDeCompras from "./components/Carrito-de-compras.vue";


export default {
    name: "App",
    components: {
        ProductoVenta,
        CarritoDeCompras,
    },
    data() {
        return {
            productos: [
                {
                    id: 1,
                    titulo: "Cocacola 500ml",
                    precio: 110,
                    nombreImagen: "cocacola.jpg",
                    destacado: false,
                },
                {
                    id: 2,
                    titulo: "Galletita Sonrisa",
                    precio: 125,
                    nombreImagen: "galletita-sonrisa.jpg",
                    destacado: false,
                },
                {
                    id: 3,
                    titulo: "Alfajor Capital del espacio",
                    precio: 150,
                    nombreImagen: "alfajor-capitan-del-espacio.jpg",
                    destacado: true,
                },
            ],
            productosEnCarrito: [],
        };
    },
    mounted() {},
    methods: {
        AgregarAlCarrito(id) {
            let result = this.productos.find((prod) => {
                return prod.id == id;
            });
            this.productosEnCarrito.push(result);
            // if (result) {
            //     this.$refs.miCarrito.AgregarProducto(result);
            // }
        },
    },
};
</script>


<style>
body {
    margin: 0;
}
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #111;
}
.contenedorProductos {
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>