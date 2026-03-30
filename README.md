```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <title>GitHub Pins Linguagens</title>
  <style>
    body {
      font-family: Arial;
      background: #0d1117;
      color: #fff;
    }
    .repo {
      background: #161b22;
      padding: 15px;
      margin: 10px;
      border-radius: 8px;
    }
  </style>
</head>
<body>

<h1>Meus Repositórios</h1>
<div id="repos"></div>

<script>
const username = "SEU_USUARIO_AQUI";

fetch(`https://api.github.com/users/${username}/repos`)
  .then(res => res.json())
  .then(data => {
    const container = document.getElementById("repos");

    data.forEach(repo => {
      // Aqui você pode filtrar manualmente os "pins"
      // Exemplo: só mostrar alguns nomes específicos
      const pinnedRepos = ["repo1", "repo2"]; 

      if (pinnedRepos.includes(repo.name)) {
        const div = document.createElement("div");
        div.className = "repo";

        div.innerHTML = `
          <h2>${repo.name}</h2>
          <p>Linguagem principal: ${repo.language}</p>
        `;

        container.appendChild(div);
      }
    });
  });
</script>

</body>
</html>
```
