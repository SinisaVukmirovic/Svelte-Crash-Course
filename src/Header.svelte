<script>

    import { Link } from 'svero';

</script>

<style>
    header {
        display: flex;
        justify-content: space-between;
        background-color: lightblue;
        padding: 1em 20%;
        font-size: 1.25rem;
        font-weight: bold;
    }

    nav ul {
        display: flex;
        list-style-type: none;
        margin: 0;
    }
        nav li {
            margin: 0 1em;
        }
</style>

<header>
    <Link href="/home" className="logo">My Svelte App</Link>

    <nav>
        <ul>
            <li><Link href="/home">Home</Link></li>
            <li><Link href="/about">About</Link></li>
        </ul>
    </nav>
</header>