<!-- ProtectedRoute.svelte -->
<script>
    import { isAuthenticated, setAuthenticated } from "./auth.js";
    import { onMount } from "svelte";

    let loading = true; // Initial loading state

    onMount(() => {
        setTimeout(() => {
            loading = false;
        }, 1000); // Simulate authentication check delay (remove this in production)
    });
</script>

{#if loading}
    <p>Loading...</p>
{:else if $isAuthenticated}
    <slot />
{:else}
    <!-- Render the login screen here -->
    <h1>Login</h1>
    <button class="btn btn-primary" on:click={() => setAuthenticated(true)}
        >Login</button
    >
{/if}

<!-- <script>
    import { isAuthenticated, setAuthenticated } from "./auth.js";
</script>

{#if $isAuthenticated}
    <slot />
{:else}
    <h1>Login</h1>
    <button class="btn btn-primary" on:click={() => setAuthenticated(true)}>Login</button>
{/if} -->
