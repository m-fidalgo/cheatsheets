<h1 align="center">WebSockets com socket.io</h1>

<h3>Uso</h3>
<p>Instalar socket.io</p>
<p>No html</p>

```
<script src="https://cdn.socket.io/socket.io-X.X.X.js"></script>
<script>
  var socket = io("http://localhost:3000");
  socket.on("server_hello", receiveMessage);

  function sendMessage() {
    //pegar o dado escrito no textarea

    socket.emit("client_hello", { text });
  }

  function receiveMessage() {
    //colocar na label
  }
</script>

```
