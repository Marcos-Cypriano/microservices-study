# Repo cloned 
    diego3g/microservices-base-decode 


# Run apps
    Por ser microsserviços, é possível rodar apenas uma aplicação sem a outra. Ex: é possível gerar uma compra só com esse serviço funcionando, quando o classroom for iniciado este irá buscar no kafka as mensagens de compras realizadas e irá realizar os novos cadastros.
    Criar os arquivos .env em cada aplicação (classroom e purchases) com as variáveis: KAFKA_BROKER e DATABASE_URL.

    root:
        docker-compose up -d (esperar o kafka iniciar, docker logs -f)
        (talvez seja necessário dar um restart no kafka)
    apps/purchase:
        yarn
        yarn prisma migrate dev
        yarn run start:dev
    apps/classroom:
        yarn
        yarn prisma migrate dev
        yarn run start:dev