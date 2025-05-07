# Configuração de Redes Internas no Docker com Redis

Criei duas redes internas no Docker: `backend` e `frontend`, ambas utilizando o driver `bridge` para permitir a comunicação interna entre os contêineres. Após a criação das redes, realizei o build de cada imagem localmente e criei os respectivos contêineres, expondo-os em suas portas apropriadas e conectando-os às redes definidas.

Inicialmente, observei apenas um erro de comunicação com o Redis. Esse problema ocorreu porque a imagem do Redis ainda não havia sido baixada e o contêiner correspondente não havia sido criado.

Em seguida, parei todos os contêineres, removi-os e executei o arquivo `docker-compose.yml` para subir novamente os serviços, dessa vez de forma conjunta e incluindo o Redis.

Após esse processo, consegui acessar as aplicações no navegador. Conforme demonstrado nos prints, o serviço de `write` estava recebendo os dados via POST e armazenando a chave no Redis. O serviço de `reader`, por sua vez, realizava o GET da chave armazenada e a exibia no `frontend`.

Após algumas pesquisas, realizei um code review e não identifiquei erros nem no código-fonte nem no arquivo `docker-compose.yml`.
