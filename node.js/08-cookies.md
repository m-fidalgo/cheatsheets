<h1 align="center">Cookies</h1>

<h3>Uso</h3>
<p>Instalar cookie-parser</p>
<p>Em app.js</p>

```
const cookieParser = require("cookie-parser");

app.use(cookieParser());

//enviar cookie
app.get("/", (req, res) => {
  res.cookies("cookie", 123, { maxAge: 1234 });
  res.send("message");
});

//pegar cookie
app.get("/", (req, res) => {
  console.log(req.cookies.cookie);
  res.send("message");
});
```
