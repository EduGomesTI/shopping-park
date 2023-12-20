# Shopping Parking System

## Objetivo

Este projeto tem por objetivo desenvolver um sistema de gerenciamento de estacionamento para Shopping Centers.

No Brasil é muito comum que os Shopping Centers cobrem pelo tempo que o cliente estiver usando o estacionamento, desta forma sse faz necessário que exista um sistema que possa gerenciar todo o processo de estadia e cobrança de cada veículo.

Uma abordagem típica de um cliente usando o sistema:

- O cliente ao entrar no shopping recebe um cartão com código de barras numa cancela eletrônica;
- Ao sair do shopping o cliente realiza a validação do cartão numa máquina ou clichê de pagamento. Geralmente existe uma tolerância de 15 minutos que não é cobrado.
- Ao validar o cartão o cliente está apto a sair do estacionamento inserindo o cartão na cancela eletrônica.

## Visão geral do Sistema

!["Visão geral do Sistema"](/out/docs/model/system_diagram/System_Context_Diagram.png)



## Visão geral da API

!["Visão geral da API"](/out/docs/model/container_diagram/Container_Context.png)

## Módulos

### Entrance Service

![Entrance Service](/out/docs/model/container_entrance/Container_Entrance_Diagram.png)

Este módulo é responsável por permitir a entrada do cliente no estacionamento do shopping.

O cliente para na frente da cancela automática e recebe um cartão com código de barras.

> A forma como o cliente irá receber o cartão, se será ao apertar um botão, de forma automática, etc, está fora do escopo do sistema.

Internamente o sistema irá gerar um objeto que irá conter o Id (Código de barras do cartão), a data e horário de entrada e a placa do veículo que será capturada através de uma camera.

Este objeto será gravado num banco de dados para posteriormente ser enviado para um message broke, após o envio o objeto poderá ser excluído do banco.

> O uso do banco de dados neste serviço se dá meramente para o uso do *Inbox Pattern*, além disso ele não tem utilidade na arquitetura.

## Payment Service

![Payment Service](/out/docs/model/container_payment/Container_Payment_Diagram.png)

## Exit Service

![Exit Service](/out/docs/model/container_exit/Container_Exit_Diagram.png)

## Master Service

![Master Service](/out/docs/model/container_master/Container_Master_Diagram.png)