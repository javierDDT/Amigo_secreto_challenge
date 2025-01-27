# Amigo_secreto_challenge
Crear codigo para almacenar nombres y poder sortearlos aleatoriamente
<!DOCTYPE html> 
<html> 
<head> 
<title>Amigo Secreto</title> 
<style> 
body { 
  font-family: sans-serif; 
} 
#amigos { 
  width: 200px; 
  height: 100px; 
  overflow-y: auto; 
  border: 1px solid #ccc; 
  padding: 5px; 
  margin-bottom: 10px; 
} 
</style> 
</head> 
<body> 
 
<h1>Amigo Secreto</h1> 
 
<input type="text" id="nombreAmigo" placeholder="Nombre del amigo"> 
<button onclick="agregarAmigo()">Adicionar</button> 
 
<div id="amigos"></div> 
 
<button onclick="sortearAmigo()" disabled id="sortear">Sortear Amigo</button> 
<p id="resultado"> 
 
<script> 
let amigos = []; 
 
function agregarAmigo() { 
  const nombre = document.getElementById("nombreAmigo").value.trim(); 
  if (nombre === "") { 
    alert("Por favor, ingrese un nombre válido."); 
    return; 
  } 
 
  if (amigos.includes(nombre)) { 
    alert("Este amigo ya está en la lista."); 
    return; 
  } 
 
  amigos.push(nombre); 
  actualizarLista(); 
  document.getElementById("nombreAmigo").value = ""; 
  document.getElementById("sortear").disabled = false; 
} 
 
function actualizarLista() { 
  const listaAmigos = document.getElementById("amigos"); 
  listaAmigos.innerHTML = ""; // Limpia la lista antes de actualizar 
  amigos.forEach(amigo => { 
    const li = document.createElement("li"); 
    li.textContent = amigo; 
    listaAmigos.appendChild(li); 
  }); 
} 
 
function sortearAmigo() { 
  if (amigos.length === 0) { 
    alert("Agrega amigos a la lista primero!"); 
    return; 
  } 
  const indiceAleatorio = Math.floor(Math.random() * amigos.length); 
  const amigoSecreto = amigos[indiceAleatorio]; 
  document.getElementById("resultado").textContent = "El amigo secreto es: " + amigoSecreto; 
} 
</script> 
 
</body> 
</html> 
