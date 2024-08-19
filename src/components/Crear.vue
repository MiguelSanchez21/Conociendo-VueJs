<template>
    <div class="container">
        <div class="card">
            <div class="card-header">
                Agregar nuevo Usuario
            </div>
            <div class="card-body">
                <form v-on:submit.prevent="agregarRegistro">
                    <div class="form-group">
                      <label for="nombre">Nombre:</label>
                      <input type="text"
                        class="form-control" required name="nombre" v-model="usuario.nombre" id="nombre" aria-describedby="helpId" placeholder="Nombre">
                      <small id="helpId" class="form-text text-muted">Escribe el nombre del usuario</small>
                    </div>
                    
                    <div class="form-group">
                      <label for="">Teléfono:</label>
                      <input type="number"
                        class="form-control" required name="telefono" v-model="usuario.telefono" id="telefono" aria-describedby="helpId" placeholder="Teléfono">
                      <small id="helpId" class="form-text text-muted">Escribe el teléfono del usuario</small>
                    </div>

                    <div class="btn-group" role="group" aria-label="">
                        <button type="submit" class="btn btn-success">Agregar</button>
                        <router-link :to="{name:'Listar'}" class="btn btn-warning">Cancelar</router-link>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data(){

        return{
            usuario:{}
        }

    },    
    methods:{
        agregarRegistro(){
            console.log(this.usuario);
        
        var datosEnviar={nombre: this.usuario.nombre,telefono: this.usuario.telefono}
        fetch('http://localhost/usuarios/?insertar=1',{
            method:"POST",
            body:JSON.stringify(datosEnviar)
        })
        .then(respuesta=>respuesta.json())
        .then((datosRespuesta=>{
            console.log(datosRespuesta);
            window.location.href='listar'
        }))
        }
    }
}
</script>