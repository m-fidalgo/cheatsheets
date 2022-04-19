<h1 align="center">Validação com Joi (Celebrate)</h1>

<h3>Início</h3>

```
npm install celebrate
```
<p>Uso da biblioteca Joi (validação para JS), integrando-a com o express</p>

<h3>Uso</h3>
<p>Em routes.js</p>

```
const { celebrate, Segments, Joi } = require("celebrate");

//exemplo -> validação body

routes.post(
  "/nomeRota",
  celebrate({
    [Segments.BODY]: Joi.object().keys({
      name: Joi.string().required(),
      email: Joi.string().required().email(),
      phone: Joi.string().required().min(10).max(11),
      uf: Joi.string().required().length(2),
    }),
  }),
  nomeController.create
);

//exemplo -> validação header
routes.get(
  "/nomeRota",
  celebrate({
    [Segments.HEADERS]: Joi.object({
      auth: Joi.string().required(),
    }).unknown(),
  }),
  nomeController.list
);

//exemplo -> validação route params
routes.delete(
  "/nomeRota/:id",
  celebrate({
    [Segments.PARAMS]: Joi.object().keys({
      id: Joi.number().required(),
    }),
  }),
  nomeController.delete
);
```
