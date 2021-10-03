<template>
  <div class="home">
    <div class="table-responsive">
      <table class="table">
        <thead>
          <tr>
            <th>Numero de factura</th>
            <th>Formato de numeracion</th>
            <th>Fecha dd/mm/yyyy</th>
            <th>Fecha de vencimiento dd/mm/yyyy</th>
            <th>Descripción</th>
            <th>Nombre del contacto</th>
            <th>CIF</th>
            <th>Dirección</th>
            <th>Población</th>
            <th>Codigo Postal</th>
            <th>Provincia</th>
            <th>País</th>
            <th>Cocepto</th>
            <th>Descripción</th>
            <th>SKU</th>
            <th>Precio unidad</th>
            <th>Unidades</th>
            <th>Descuento %</th>
            <th>IVA %</th>
            <th>Retención %</th>
            <th>Rec. de eq. %</th>
            <th>Operacion</th>
            <th>Forma de pago (ID)</th>
            <th>Cantidad cobrada</th>
            <th>Fecha de cobro</th>
            <th>Cuenta de pago</th>
            <th>Tags separados por -</th>
            <th>Nombre canal de venta</th>
            <th>Cuenta canal de venta</th>
            <th>Moneda</th>
            <th>Cambio</th>
          </tr>
        </thead>
        <tbody>
          <template v-for="(factura, i) in facturas.slice(23, 28)" :key="i">
            <tr v-for="linea in factura.lines">
              <td>
                <template v-if="factura.number">
                  {{ factura.number }}
                </template>
              </td>
              <td>
                [YY]%%%%
              </td>
              <td>
                <template v-if="factura.date">
                  {{ factura.date }}
                </template>
              </td>
              <td>
                <template v-if="factura.dueDate">
                  {{ factura.dueDate }}
                </template>
              </td>
              <!-- Descripción -->
              <td></td>
              <!-- Nombre del contacto -->
              <td></td>
              <!-- Cif -->
              <td>
                <template v-if="factura.customerCiNumber">
                  {{ factura.customerCiNumber }}
                </template>
              </td>
              <!-- Dirección -->
              <td></td>
              <!-- Población -->
              <td></td>
              <!-- Codigo postal -->
              <td></td>
              <!-- Provincia -->
              <td></td>
              <!-- Pais -->
              <td></td>

              <td style="width: 200px;">
                {{ linea.productName }}
              </td>
              <td style="width: 200px;">
                {{ linea.description }}
              </td>
              <td>
                {{ linea.productSku }}
              </td>

              <td>
                {{ linea.unitNetPrice }}
              </td>

              <td style="width: 100px;">
                {{ linea.quantity }}
              </td>
              <td>
                {{ linea.lineDiscountRate }}
              </td>

              <td>
                <template v-if="linea.taxRate === 21">s_iva_21</template>
                <template v-else-if="linea.taxRate === 10">s_iva_10</template>
                <template v-else-if="linea.taxRate === 4">s_iva_4</template>
                <template v-else-if="linea.taxRate === 0">s_iva_0</template>
              </td>
              <td>
                {{ linea.incomeTaxDeductionRate }}
              </td>
              <td>0</td>
              <td>general</td>
              <td>5ff34baf600d93174a0f7645</td>
              <td style="">
                <template v-if="i === i">
                  <div v-for="(pago, i) in factura.payments" :key="i">
                    {{ pago.amount }}
                  </div>
                </template>
              </td>
              <td style="">
                <div v-for="pago in factura.payments">
                  {{ pago.paymentDate }}
                </div>
              </td>

              <td>
                <div v-for="(pago, i) in factura.payments" :key="i">
                  57200001
                </div>
              </td>
              <td></td>
              <td>
                Ventas
              </td>
              <td>70500000</td>

              <td>
                {{ factura.currency.toLowerCase() }}
              </td>
              <td>
                1
              </td>
            </tr>
          </template>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Products from "@/views/json/facturas.json";

export default defineComponent({
  name: "Home",
  components: {
    Products,
  },
  data() {
    return {
      facturas: Products,
    };
  },
});
</script>

<style lang="scss">
.table {
  font-size: 0.7rem;
}
</style>
