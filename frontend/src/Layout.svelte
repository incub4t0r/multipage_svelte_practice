<!-- Layout.svelte -->
<script>
    // Access the current page's path from SvelteKit's $page variable
    import { page } from "$app/stores";

    // Define an array of navigation links with their href values
    const navLinks = [
        { text: "Home", href: "/" },
        { text: "About", href: "/about" },
        { text: "Feed", href: "/feed" },
        { text: "Settings", href: "/settings" },
    ];
</script>

<header>
    <!-- <p>Current URL: {$page.route.id}</p> -->
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">Navbar</a>
            <button
                class="navbar-toggler"
                type="button"
                data-bs-toggle="collapse"
                data-bs-target="#navbarNav"
                aria-controls="navbarNav"
                aria-expanded="false"
                aria-label="Toggle navigation"
            >
                <span class="navbar-toggler-icon" />
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
                <ul class="navbar-nav">
                    {#each navLinks as link}
                        <li class="nav-item">
                            <a
                                class="nav-link"
                                href={link.href}
                                class:active={$page.route.id === link.href}
                                aria-current={$page.route.id === link.href
                                    ? "page"
                                    : null}
                            >
                                {link.text}
                            </a>
                        </li>
                    {/each}
                </ul>
            </div>
        </div>
    </nav>
</header>

<main>
    <div class="container-lg">
        <slot />
    </div>
</main>
