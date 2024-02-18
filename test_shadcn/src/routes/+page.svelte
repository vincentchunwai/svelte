<script lang="ts">
    export let params;
    import DataTable from "./auth/data-table.svelte";
    import Button from "$lib/components/ui/button/button.svelte";
    import "carbon-components-svelte/css/g100.css";
    import { Modal } from "carbon-components-svelte";
    import Header from "../components/header.svelte";

    let open = false;

</script>
  <div class="container mx-auto py-10">
    
    
    <Header/>
    <Button class="my-4" on:click={() => open =true}> Register User </Button>
    <DataTable />
    <Modal
    bind:open
    modalHeading="Add User"
    primaryButtonText="Confirm"
    secondaryButtonText="Cancel"
    on:click:button--secondary={() => (open = false)}
    on:open
    on:close
    on:submit
  >
    <p>Enter User Details</p>
  </Modal>
</div>
