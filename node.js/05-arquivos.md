<h1 align="center">Streaming e Arquivos</h1>

<h3>Streaming</h3>
<p>Transmissão de dados em pacotes</p>

```
const fs = require('fs');
const http = require('http');
const url = require('url');

http.createServer((req, res) => {
  if (req.url === "/movie.mp4") {
    const file = path.resolve(__dirname, "movie.mp4");
    const range = req.headers.range;
    const positions = range.replace("/bytes=/", "").split("-");
    const start = parseInt(positions[0], 10);

    fs.stat(file, (err, stats) => {
      const total = stats.size;
      const end = positions[1] ? parseInt(positions[1], 10) : total - 1;
      const chunkSize = end - start + 1;

      res.writeHead(200, {
        "Content-Range": "bytes" + start + "-" + end + "/" + total,
        "Accept-Ranges": "bytes",
        "Content-Length": chunkSize,
        "Content-Type": "video/mp4",
      });

      const stream = fs
        .createReadStream(file, { start, end })
        .on("open", () => stream.pipe(res))
        .on("error", (err) => res.end(err));
    });
  }
});
```
