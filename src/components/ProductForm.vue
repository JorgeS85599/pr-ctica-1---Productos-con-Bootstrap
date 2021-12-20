<template>
      <div class="row">
            <div class="col-sm-6 col-md-4 col-lg-4 hide" id="form">
                <form id="new-prod">
                    <fieldset>
                        <legend>Nuevo producto</legend>
                        <!-- Aquí los inputs y botones del form -->
                        <label for="newprod-id" id="newprod-id-label">Id: </label><br>
                        <input type="number" id="newprod-id-input" name="newprod-id" disabled><br>
                        <label for="newprod-name">Nombre: </label><br>
                        <input type="text" id="newprod-name" name="newprod-name" required minlength="3" v-model="newProd.name"><br>
                        <label for="newprod-price">Precio/u: </label><br>
                        <input type="number" id="newprod-price" name="newprod-price" step="0.01" value="0.00" placeholder="0.00" v-model.number="newProd.price"><br>
                        <label for="newprod-units" id="newprod-units-label" class="hide">Unidades: </label><br>
                        <input type="number" id="newprod-units-input" class="hide" name="newprod-units" min="0" step="1" v-model.number="newProd.units"><br>
                        <button @click="addProduct" type="submit" class="btn btn-default btn-primary">Añadir</button>
                        <button type="reset" class="btn btn-danger">Reset</button>
                    </fieldset>
                </form>
            </div>
        </div>
</template>

<script>
export default {
    name: 'product-form',
    data() {
        return {
            newProd: {

                name:'',
                price:'',
                units: ''
            }
        }
    },
    methods: {
        addProduct() {

            if (this.newProd) { 
                this.$emit("add-product",this.newProd)
                this.newProd = {}
            }
            
        }
        
    }
}
</script>