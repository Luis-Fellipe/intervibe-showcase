# InterVibe

> Rede social para **praticar idiomas e fazer amigos**: conecta pessoas que querem praticar idiomas através da conversação.

Projeto autoral full stack, que planejei, desenvolvi e publiquei sozinho, cuidando de todas as etapas, do front-end ao servidor.

> 🔒 **O código-fonte é privado**, porque o InterVibe foi pensado como um produto real. Este repositório apresenta o projeto, as decisões técnicas e os desafios que enfrentei. Posso mostrar o código em uma entrevista.
>
> ⏸️ **Status:** desenvolvimento pausado e servidores desativados por enquanto. Demonstração em vídeo e capturas de tela em breve.

---

## ✨ Funcionalidades

- Cadastro e login com **verificação de e-mail** e **recuperação de senha**
- Interface **multilíngue** (português, inglês e espanhol)
- Instalável como aplicativo (**PWA**), com interface pensada para celular e tema escuro

---

## 🛠️ Tecnologias

| Camada | Tecnologias |
|---|---|
| Front-end | HTML · CSS · JavaScript puro (sem framework) · PWA |
| Back-end | Node.js · Fastify · TypeScript |
| Banco de dados | MySQL |
| Infraestrutura | HostGator (front-end) · Railway (back-end e banco) · deploy via SFTP |

---

## 🏗️ Arquitetura

```
 Usuário (navegador / PWA)
          │
          ▼
 Front-end estático ──── HostGator
          │  requisições HTTP
          ▼
 API Node.js + Fastify ── Railway
          │
          ▼
       MySQL ──────────── Railway
```

---

## 🧩 Desafios e decisões técnicas

**Hospedagem dividida para reduzir custos.**
A HostGator não roda Node.js, então separei o projeto: o front-end estático ficou na HostGator e a API com o banco foram para a Railway. Comparei também a Vercel e escolhi a combinação que deixava o custo mensal mais baixo para um projeto em fase inicial.

**Build do back-end com `tsc`.**
O `tsup` gerava um build incompatível com o uso de `await` no nível superior do código. Passei a compilar com o próprio `tsc` e a rodar a versão compilada carregando as variáveis de ambiente pelo próprio Node.

**Fluxo de verificação de e-mail.**
O link enviado no e-mail apontava para o front-end em vez da API. Corrigi a rota para que a verificação fosse processada pelo back-end antes de redirecionar o usuário.

**Front-end sem framework.**
Construí toda a interface com HTML, CSS e JavaScript puro, incluindo a troca de idioma da interface, o que me obrigou a organizar o código por páginas e módulos sem depender de bibliotecas.

**Experiência de app no celular (PWA).**
Ajustei o comportamento para parecer um aplicativo nativo: bloqueei o zoom por gesto de pinça e corrigi o estilo do preenchimento automático do navegador, que quebrava o tema escuro.

---

## 📚 O que aprendi

- Planejar um produto do zero e dividir o trabalho entre front-end, back-end e infraestrutura
- Colocar uma aplicação no ar e mantê-la, considerando custo de hospedagem

---

## 👤 Autor

**Luís Fellipe**
[LinkedIn](https://www.linkedin.com/in/luis-fellipe-real/) · [GitHub](https://github.com/Luis-Fellipe)
