<h1>Desafio Full Cycle - Imagem Docker Go</h1>

<p>Este é um projeto emocionante, especialmente se você nunca trabalhou com a linguagem Go! O desafio é criar uma imagem Docker que, quando executada, exibirá a mensagem "Full Cycle Rocks!!".</p>

<h2>Requisitos</h2>

<ul>
    <li>A imagem Docker deve ser publicada no Docker Hub.</li>
    <li>A imagem resultante deve ter menos de 2MB.</li>
</ul>

<h2>Como usar</h2>

<p>Para executar esta imagem, certifique-se de ter o Docker instalado em seu sistema e execute o seguinte comando:</p>

<pre><code>docker run roineybeal/fullcycle</code></pre>

<p>Você verá a seguinte saída:</p>

<pre><code>Full Cycle Rocks!!</code></pre>

<h2>Construindo a imagem</h2>

<p>O Dockerfile deste projeto é configurado da seguinte maneira:</p>

<pre><code>
# Estágio 1: Compilação do código Go
FROM golang:alpine AS builder

WORKDIR /src
COPY . .

RUN go build -ldflags '-s -w' main.go

# Estágio 2: Construção da imagem final
FROM scratch

WORKDIR /

COPY --from=builder /src /

CMD ["./main"]
</code></pre>

<p>No <strong>Estágio 1</strong>, usamos a imagem <code>golang:alpine</code> como base para compilar nosso código Go. Definimos o diretório de trabalho como <code>/src</code> e copiamos todos os arquivos do projeto para esse diretório. Em seguida, usamos o comando <code>go build</code> para compilar o arquivo <code>main.go</code>. Isso cria um executável chamado <code>main</code>.</p>

<p>No <strong>Estágio 2</strong>, usamos a imagem <code>scratch</code> como base, que é uma imagem mínima e vazia. Copiamos o executável <code>main</code> do Estágio 1 para a raiz da imagem. Em seguida, definimos o comando padrão para ser executado quando a imagem Docker for iniciada, que é <code>./main</code>.</p>

<h2>Imagem Docker</h2>

<p>A imagem Docker resultante deste projeto pode ser encontrada no Docker Hub através do seguinte link:</p>

<p><a href="https://hub.docker.com/r/roineybeal/fullcycle">roineybeal/fullcycle</a></p>

<h2>Repositório Git</h2>

<p>O código-fonte deste projeto está disponível em um repositório Git remoto. Você pode acessá-lo <a href="https://github.com/seu-usuario/nome-do-repositorio">aqui</a>.</p>

<p>Divirta-se codificando e Dockerizando! 😊🚀</p>

</body>
</html>