A ideia para resolver o problema de compra de ingressos descartando a interferencia da velocidade de internet pode ser resolvida com o uso de Filas.

Para isso, utilizaria o protocolo de mensagens assíncronas(AMQP) que permite a comunicação entre diferentes sistemas distribuídos

Dessa forma, a aplicação faria um publish para exchange que é o responsavel por encaminhar as mensagens para a fila/topico especifico, que no nosso caso terá apenas uma fila/topico nomeada "ingressos", onde um serviço estaria ouvindo esse topico para realizar as operações e controlar a quantidade de ingressos para compra. O serviço que teria feito o subscribe nesse topico seria o backend da aplicação que vende ingressos para o Rock em Rio. Com isso o backend teria controle da quantidade de ingressos disponiveis pelo banco de dados e a quantidade de ingressos que estão sendo requisitados para compra através da lista. Sendo implementado uma logica para controlar o acesso aos ingressos até que se finalize.


FRONTEND = INTERFACE WEB/MOBILE/DESKTOP.
BROKER = Gerenciador de filas, onde garante a entrega correta e ordenada das mensagens aos destinatários(subscribers).
