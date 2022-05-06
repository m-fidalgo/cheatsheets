<h1 align="center">JWT</h1>

<h3>Introdução</h3>
<p>Instalar jsonwebtoken e importar como jwt onde será usado</p>

<h3>Login</h3>

```
async create(req res) {
  const {email, password} = req.body;
  const user = await connection('user')
    .where('email', email)
    .where('password', password)
    .select('*')
    .first()
  
  //verificar antes se o jwt foi encontrado
  const token = jwt.sign({user.id}, "secret", {
    expiresIn: 86400
  });
  
  return res.json({auth: true, token})
}
```
<h3>Logout</h3>

```
async logout(req, res) {
  res.json({auth: false, token: null})
}
```
<h3>Verificação (Autorização)</h3>
<p>Para todas as requisições que exigem que o usuário esteja logado</p>

```
function verifyJwt(req, res, next) {
  const token = req.headers['x-access-token'];
  if(!token) return res.status(401).json({auth: false, message: 'No token'});
  jwt.verify(token, "secret", (err, decoded) => {
    if(err) return res.status(500).json({auth: false, message: 'Failed to auth'});
    req.userId = decoded.id;
    next();
  })
}
```
