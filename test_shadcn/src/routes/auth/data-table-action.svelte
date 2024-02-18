<script lang="ts">
    import * as DropdownMenu from "$lib/components/ui/dropdown-menu";
    import { Button } from "$lib/components/ui/button";
    import { Checkbox } from "$lib/components/ui/checkbox";
    import { Label } from "$lib/components/ui/label";
    import { MoreHorizontal } from "lucide-svelte";
    import "carbon-components-svelte/css/g10.css";
    import { Modal } from "carbon-components-svelte";
    export let email: string;

    let open_credential = false;
  </script>
  <DropdownMenu.Root>
    <DropdownMenu.Trigger asChild let:builder>
      <Button
        variant="ghost"
        builders={[builder]}
        size="icon"
        class="relative w-8 h-8 p-0"
      >
        <span class="sr-only">Open menu</span>
        <MoreHorizontal class="w-4 h-4" />
      </Button>
    </DropdownMenu.Trigger>
    <DropdownMenu.Content>
      <DropdownMenu.Group>
        <DropdownMenu.Label>Actions</DropdownMenu.Label>
        <DropdownMenu.Item on:click={() => navigator.clipboard.writeText(email)}>
          Copy User email
        </DropdownMenu.Item>
      </DropdownMenu.Group>
      <DropdownMenu.Separator />
      <DropdownMenu.Item on:click={() => open_credential = true}>check credential</DropdownMenu.Item>
      <!-- <DropdownMenu.Item>View payment details</DropdownMenu.Item> -->
    </DropdownMenu.Content>
  </DropdownMenu.Root>

  <Modal
    bind:open={open_credential}
    modalHeading="Authorize User"
    
    on:click:button--secondary={() => (open_credential = false)}
    on:open
    on:close
    primaryButtonText="Confirm"
    secondaryButtonText="Cancel"
  >
    <div class="items-top flex space-x-2 my-3">
      <Checkbox id="Centrallock" />
      <div class="grid gap-1.5 leading-none">
        <Label
          for="Centrallock"
          class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
        >
          Centrallock access right
        </Label>
        <!-- <p class="text-sm text-muted-foreground">
          You agree to our Terms of Service and Privacy Policy.
        </p> -->
      </div>
    </div>
    <div class="items-top flex space-x-2 my-3">
      <Checkbox id="CentralDoc" />
      <div class="grid gap-1.5 leading-none">
        <Label
          for="CentralDoc"
          class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
        >
          CentralDoc access right
        </Label>
        <!-- <p class="text-sm text-muted-foreground">
          You agree to our Terms of Service and Privacy Policy.
        </p> -->
      </div>
    </div>
    <div class="items-top flex space-x-2 my-3">
      <Checkbox id="Ticket123" />
      <div class="grid gap-1.5 leading-none">
        <Label
          for="Ticket123"
          class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
        >
          Ticket123 access right
        </Label>
        <!-- <p class="text-sm text-muted-foreground">
          You agree to our Terms of Service and Privacy Policy.
        </p> -->
      </div>
    </div>
  </Modal>