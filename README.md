<h1 align="center">Hi 👋, I'm João Gouveia <img height="40" src="https://64.media.tumblr.com/3848e5ce9550ab723c4c17ae5c2c830d/cbbf628e3f78039b-9c/s1280x1920/b184a988a5bd644f8a98544c2624d362aef3094c.gifv"></h1>
<h3 align="center">I am a Front-Back End Developer!</h3>

<!-- - 🔭 I’m currently working on my **Python Course** -->

- 🌱 I’m currently learning **C#**

- 👯 I’m looking to collaborate on **front-end and back-end projects**

- 📫 How to reach me: **joao.daniel.gouveia2001@gmail.com**

- ⚡ What I like to do: **I like to play videogames with friends and Eat!**


<h3 align="center">Connect with me:</h3>
<div align="center">

[![image](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/jo%C3%A3o-gouveia-8496131b6/)
[![image](https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/itzgouveiaa/)

</div>

<h3 align="center">Languages and Tools:</h3>

<p align="center">
  <a href="https://www.w3.org/html/" target="_blank">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg" alt="html5" width="40" height="40"/>
  </a>
  <a href="https://www.w3schools.com/css/" target="_blank">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original-wordmark.svg" alt="css3" width="40" height="40"/>
  </a>
  <a href="https://www.java.com/pt-BR/" target="_blank">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg" alt="Java" width="40" height="40"/>
  </a>  
  
  <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="javascript" width="40" height="40"/>
  </a>
  <a href="https://www.php.net/" target="_blank">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-plain.svg" alt="PHP" width="40" height="40"/>
  </a>
  <a href="https://pt.wikipedia.org/wiki/C_(linguagem_de_programa%C3%A7%C3%A3o)" target="_blank">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/c/c-line.svg" alt="C" width="40" height="40"/>
  </a>
  <a href="https://learn.microsoft.com/en-us/dotnet/csharp/" target="_blank">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/csharp/csharp-line.svg" alt="C#" width="40" height="40"/>
  </a>
  <a href="https://git-scm.com/" target="_blank">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" alt="Git" width="40" height="40"/>
  </a>
   <a href="https://www.adobe.com/?mv=affiliate&mv2=red" target="_blank">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/photoshop/photoshop-line.svg" alt="Photoshop" width="40" height="40"/>
  </a>
   <a href="https://www.adobe.com/?mv=affiliate&mv2=red" target="_blank">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/illustrator/illustrator-line.svg" alt="Illustrator" width="40" height="40"/>
  </a>
  <a href="https://www.adobe.com/?mv=affiliate&mv2=red" target="_blank">
    <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/aftereffects/aftereffects-plain.svg" alt="AfterEffects" width="40" height="40"/>
  </a>
</p>


 ![GitHub stats](https://github-readme-stats.vercel.app/api?username=JoaoGouveia24&show_icons=true&theme=radical)

 [![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=JoaoGouveia24&layout=compact)](https://github.com/JoaoGouveia24/github-readme-stats)

<br><br>

# GitHub Action for generating a contribution graph with a snake eating your contributions.

name: Generate Snake

# Controls when the action will run. This action runs every 6 hours.

on:
  schedule:
      # every 6 hours
    - cron: "0 */6 * * *"

# This command allows us to run the Action automatically from the Actions tab.
  workflow_dispatch:

# The sequence of runs in this workflow:
jobs:
  # This workflow contains a single job called "build"
  build:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:

    # Checks repo under $GITHUB_WORKSHOP, so your job can access it
      - uses: actions/checkout@v2

    # Generates the snake  
      - uses: Platane/snk@master
        id: snake-gif
        with:
          github_user_name: JoaoGouveia24
          # these next 2 lines generate the files on a branch called "output". This keeps the main branch from cluttering up.
          gif_out_path: dist/github-contribution-grid-snake.gif
          svg_out_path: dist/github-contribution-grid-snake.svg

     # show the status of the build. Makes it easier for debugging (if there's any issues).
      - run: git status

      # Push the changes
      - name: Push changes
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: master
          force: true

      - uses: crazy-max/ghaction-github-pages@v2.1.3
        with:
          # the output branch we mentioned above
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
