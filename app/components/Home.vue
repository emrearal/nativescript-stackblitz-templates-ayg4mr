<template>
  <Page>
    <ActionBar title="Düğme Örneği">
      <NavigationButton
        text="Go back"
        android.systemIcon="ic_menu_back"
        @tap="goBack"
      />
    </ActionBar>

    <StackLayout>
      <Button text="Action Dialog'u Aç" @tap="openActionDialog" />
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
import { ActionDialog } from '@nativescript/core';
export default {
  data() {
    return {
      counter: 0,
      showChildComponent: false,
      listOfItems: ['anan', 'baban', 'kardeşin'],
    };
  },
  methods: {
    openActionDialog() {
      const options = {
        title: 'Action Dialog',
        message: 'Bu bir action dialog örneğidir.',
        actions: ['Seçenek 1', 'Seçenek 2', 'Seçenek 3'],
        cancelButtonText: 'İptal',
      };

      ActionDialog.show(options).then((result) => {
        console.log('Seçilen indeks:', result);
      });
    },

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
