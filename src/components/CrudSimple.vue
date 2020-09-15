<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col-md-6">
                    <div class="card">
                        <div class="card-body">

                            <form v-on:submit="agregarTareas">
                               
                                <input type="text"
                                     v-model="usuarios.titulo" 
                                     class="form-control" 
                                     placeholder="titulo" >

                                <textarea  
                                   name="descripcion" 
                                    v-model="usuarios.descripcion" 
                                    class="form-control mt-2" 
                                    placeholder="descripcion">
                                </textarea>

                                <button class="btn btn-primary mt-2 btn-block">Enviar</button>
                            </form>
                        </div>
                    </div>
                </div> <!--fin columna-->

                <div class="col-md-6">
                    <table class="table">
                        <thead>
                            <tr>
                                <th>titulo</th>
                                <th>descripcion</th>
                            </tr>
                        </thead>
                            <tbody>
                                <tr v-for="(useres,index) in users" v-bind:key="index">

                                   <td> {{useres.titulo}}</td>
                                   <td> {{useres.descripcion}}</td>

                                  <button class="btn btn-danger" 
                                          v-on:click="eliminarTarea(useres)">
                                          Eliminar
                                  </button>

                                </tr>
                            </tbody>
                        
                    </table>
                </div>
            </div>
        </div>
 
    </div>
</template>

<script>

export default {
    data() {
        return { 
            users:[
                    {
                         
                        titulo:"Jonathan B",
                        descripcion:"Engenier software"
                    },
                    {
                       
                        titulo:"Ana G",
                        descripcion:"Enegenier Civil"
                    },
                    {
                        
                        titulo:"Abel B",
                        descripcion:"Abogado"
                    }
                ],
             usuarios :{},
        }
    },

    methods: {
        agregarTareas: function(e){
            e.preventDefault();
            this.users.push(this.usuarios); // lo que tenga el arrays USUARIOS insertalo en el json
            this.usuarios = {} //reinicia el input
        },

        eliminarTarea :function(usu){
            this.users.splice(usu,1); // lo que tenga el json elimina el usuario que se haga click 
        }
    },


}
</script>



<style lang="stylus">


</style>