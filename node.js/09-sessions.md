<h1 align="center">Sessions</h1>

<h3>Sobre</h3>
<p>Armazenadas no servidor</p>

<h3>Uso</h3>
<p>Instalar express-session</p>

```
const expressSession = require("express-session");

app.use(expressSession({ secret: token }));

//guardar session
app.get("/:id", (req, res) => {
  req.session.nomeSession = req.params.id;
  res.send("message");
});

//pegar session
app.get("/", (req, res) => {
  console.log(req.session.nomeSession);
  res.send("message");
});
```
