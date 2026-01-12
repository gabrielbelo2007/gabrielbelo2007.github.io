---
layout: default
title: Categorias
permalink: /categorias/
---

<div class="terminal-interface">
  
  <div class="terminal-menu">
    <div class="menu-header">
      <span>ROOT_ACCESS > SELECT_MODULE:</span>
    </div>
    
    <ul class="category-list">
      {% for category in site.categories %}
        {% assign cat_slug = category[0] | slugify %}
        <li class="terminal-option" onclick="openCategory('{{ cat_slug }}', this)">
          <span class="cmd-arrow">></span> {{ category[0] }} <span class="count">[{{ category[1].size }}]</span>
        </li>
      {% endfor %}
    </ul>
    <div class="system-status">WAITING FOR INPUT...</div>
  </div>

  <div class="terminal-display">
    <div id="welcome-msg" class="category-content active">
      <h2>// SYSTEM_READY</h2>
      <p>Selecione uma categoria no menu para acessar os arquivos.</p>
    </div>

    {% for category in site.categories %}
      {% assign cat_slug = category[0] | slugify %}
      <div id="{{ cat_slug }}" class="category-content" style="display: none;">
        <h2>// INDEX_OF: {{ category[0] }}</h2>
        <div class="file-list">
          {% for post in category[1] %}
            <div class="file-item">
              <span class="file-perm">-rwxr-xr-x</span>
              <span class="file-date">{{ post.date | date: "%Y-%m-%d" }}</span>
              <a href="{{ site.baseurl }}{{ post.url }}" class="file-name">{{ post.title }}</a>
            </div>
          {% endfor %}
        </div>
      </div>
    {% endfor %}
  </div>

</div>

<script>
  function openCategory(catId, element) {
    // Esconde todas as categorias
    var contents = document.getElementsByClassName("category-content");
    for (var i = 0; i < contents.length; i++) {
      contents[i].style.display = "none";
      contents[i].classList.remove("active");
    }

    // Remove classe ativa de todos os botões do menu
    var options = document.getElementsByClassName("terminal-option");
    for (var i = 0; i < options.length; i++) {
      options[i].classList.remove("selected");
    }

    // Mostra a categoria selecionada
    document.getElementById(catId).style.display = "block";
    
    // Marca o botão como selecionado visualmente
    element.classList.add("selected");
    
    // Atualiza status (efeito visual)
    document.querySelector('.system-status').innerText = "LOADING: " + catId.toUpperCase() + "... DONE";
  }
</script>