<template>
<div class="cards">
    <h1>Social Media Card(s)</h1>
    <div class="services">
    <div class="content content-1">
        <div class="fab fa-github">
            <h2>GitHub</h2>
            <p>So, what makes GitHub so special? Git is a command-line tool, but the center around which all things involving Git revolve is the hub—GitHub.com—where developers store their projects and network with like minded people.</p>
            <a href="https://github.com/IgorBorgess" target="_blank">Find Me</a>
        </div>
    </div>
    <div class="content content-2">
        <div class="fab fa-linkedin">
            <h2>LinkedIn</h2>
            <p>LinkedIn is the world's largest professional network on the internet. You can use LinkedIn to find the right job or internship, connect and strengthen professional relationships, and learn the skills you need to succeed in your career.</p>
            <a href="https://www.linkedin.com/in/igor-borges-357250222/" target="_blank">Find Me</a>
        </div>
    </div>
    <div class="content content-3">
        <div class="fab fa-discord">
            <h2>Discord</h2>
            <p>Discord is a free voice, video, and text chat app that's used by tens of millions of people to talk and hang out with their communities and friends. It's a home for communities of any size, but it's most widely used by small and active groups of people who talk regularly.</p>
            <a href="https://www.discordapp.com/users/302241050834108417" target="_blank">Find Me</a>
        </div>
    </div>
</div>
</div>
</template>

<script>
export default {

}
</script>

<style scoped>

    .cards {
        background-color: rgba(52,28,108,0.6);
        height: 75vh;
        max-width: 100vw;
        margin: 0 auto;
        text-align: center;
        padding: 20px;
    }

    .cards h1 {
        font-size: 40px;
        margin: 0 0 30px 0;
        text-transform: uppercase;
        letter-spacing: 1px;
    }

    .services {
        display: flex;
        align-items: center;
    }

    .content {
        display: flex;
        flex-wrap: wrap;
        flex: 1;
        margin: 20px;
        padding: 20px;
        border: 2px solid black;
        border-radius: 4px;
        transition: all 0.3s ease;
    }

    .content .fab {
        font-size: 70px;
        margin: 16px 0;
    }

    .content > * {
        flex: 1 1 100%;
    }

    .content:hover {
        color: white;
    }

    .content:hover a {
        border-color: white;
        background: white;
    }

    .content-1:hover {
        border-color: 333;
        background: #333;
    }

    .content-1:hover a{
        color: #333;
    }

    .content-2:hover {
        border-color: #1DA1F2;
        background: #1DA1f2;
    }

    .content-2:hover a{
        color: #1DA1F2;
    }

    .content-3:hover {
        border-color: #5865F2;
        background: #5865F2;
    }

    .content-3:hover a{
        color: #5865F2;
    }

    .content h2 {
        font-size: 30px;
        margin: 16px 0;
        letter-spacing: 1px;
        text-transform: uppercase;
    }

    .content p {
        font-size: 17px;
        margin-bottom: 20px;
    }

    .content a {
        margin: 22px 0;
        padding: 0.25rem;
        font-size: 50px;
        background: black;
        color: white;
        text-decoration: none;
        text-transform: uppercase;
        border: 1px solid black;
        border-radius: 25px;
        transition: 0.3s ease;
    }

    .content a:hover {
        border-radius: 4px;
    }

</style>