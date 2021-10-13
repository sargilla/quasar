<template>
  <q-page padding class="flex flex-center">
    <!-- content -->

    <div class="full-width" style="max-width: 300px">
      <h5 class="q-my-sm text-center">Login</h5>
      <q-card>
        <q-form>
          <q-card-section>
            <q-input
              label="Email"
              filled
              placeholder="email@dominio.com"
              class="q-mb-md"
            ></q-input>
            <q-input
              label="Password"
              filled
              type="password"
              placeholder="Ingrese su password"
              class="q-mb-sm"
            ></q-input>
            <q-checkbox :model-value="true" label="Recordarme" />
          </q-card-section>
          <q-btn class="full-width" color="primary">Ingresar</q-btn>
        </q-form>
      </q-card>
    </div>
  </q-page>
</template>

<script>
export default {
  // name: 'PageName',
};
</script>
