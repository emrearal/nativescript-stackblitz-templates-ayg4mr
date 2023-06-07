<template>
  <Page>
    <ActionBar title="Düğme Örneği" />
    <StackLayout>
      <Button text="Arttır" @tap="increaseCounter" />
      <Button text="Başka Bileşeni Aç" @tap="openChildComponent" />
      <Label :text="counter.toString()" />
      <Label :text="showChildComponent.toString()" />

      <Label v-if="showChildComponent" text="Başka Bileşen" />
      <Button
        v-if="showChildComponent"
        text="Kapat"
        @tap="closeChildComponent()"
      />
    </StackLayout>
  </Page>
</template>

<script>
export default {
  data() {
    return {
      counter: 0,
      showChildComponent: false,
    };
  },
  methods: {
    increaseCounter() {
      this.counter += 1;
    },
    openChildComponent() {
      this.showChildComponent = true;
    },
    closeChildComponent() {
      this.showChildComponent = false;
    },
  },
};
</script>
