# Minha Lojinha — Modelo de Análise Orientada a Objetos

Modelo de análise e projeto orientado a objetos (APOO) para o sistema de gestão do brechó de vestuário feminino multimarcas **"Minha Lojinha"**, microempreendimento situado na Muzema, Rio de Janeiro, que opera de forma híbrida entre loja física e plataformas digitais (Instagram, Mercado Livre, Shopee e Enjoei).

Projeto de Extensão III — disciplina de Análise Orientada a Objetos, Engenharia e Ciências da Computação, Universidade Veiga de Almeida (2025/2).

---

## O problema

O brechó operava com processos informais e intuitivos. A aquisição de mercadorias é oportunista, sem fornecedores fixos, e o ciclo de vida de cada peça é longo e cheio de regras: monitoramento de tempo em estoque, gatilhos de redivulgação e promoção, fila de reservas para clientes de confiança, política de preços dupla e baixa sincronizada na venda.

Sem sistema, a proprietária não conseguia calcular o lucro real nem embasar decisões de compra e precificação em dados.

## O que foi modelado

O levantamento junto à proprietária, feito por questionário estruturado, resultou em **11 requisitos funcionais** e **7 regras de negócio**, que deram origem a 8 diagramas UML.

Regras de negócio que mais impactaram o modelo:

- Pagamento em dinheiro ou Pix tem desconto obrigatório — daí os dois preços de etiqueta por peça
- Peça parada há 1 mês dispara alerta de redivulgação; passados mais 15 dias, exige desconto maior
- Promoções não são cumulativas: prevalece sempre o maior desconto
- Reserva é exclusiva para cliente de confiança (mais de 10 compras, sendo a última nos últimos 3 meses)
- Havendo mais de uma reserva para a mesma peça, forma-se fila por ordem de chegada
- Peças com mais de 3 meses em estoque são destinadas à doação

## Diagramas

| Diagrama | O que representa |
|---|---|
| Caso de uso | 11 casos de uso com a proprietária como ator primário, incluindo relação *extends* entre fila de prioridade e reserva |
| Classes | 6 classes principais — Peça de Roupa, Venda, Promoção, Reservar, Cliente e TipoPeça — com atributos, métodos e cardinalidades |
| Estados (peça) | Ciclo de vida: Disponível → Reservado → Vendido, com ramificações para cancelamento e doação |
| Estados (reserva) | Em andamento → Confirmado ou Cancelado |
| Sequência (manter peça) | Fluxo completo de CRUD entre as camadas Visão, Controle, Peça e DAO |
| Sequência (relatório de tempo) | Consulta de peças ativas e exportação do relatório |
| Sequência (criar promoção) | Três fluxos alternativos: peça individual, tipo de peça e loja toda |
| Implantação | Arquitetura em camadas: interface, aplicação em JVM e servidor de banco de dados SQL |

Os casos de uso críticos (Manter Peça de Roupa, Gerar Relatórios de Tempo de Peça e Criar Promoção) estão descritos em detalhe, com fluxo principal, fluxos alternativos e fluxos de exceção.

## Arquivos

```
.
├── Relatorio_Extensao_Minha_Lojinha.pdf   # Relatório completo com todos os diagramas
├── Desafio_1_Cronograma.pdf               # Cronograma de atividades
└── Desafio_2_ODS.pdf                      # Alinhamento com a ODS 12
```

## ODS

O projeto se alinha ao **ODS 12 — Consumo e Produção Responsáveis**. Além do ganho operacional pela redução do uso de papel e do tempo gasto em controles manuais, o próprio negócio modelado é de moda de segunda mão, prolongando o ciclo de vida das peças de vestuário.

## Metodologia e ferramentas

Análise Orientada a Objetos · UML · Levantamento de requisitos por entrevista estruturada · Modelagem estrutural e comportamental

Referências principais: Bezerra (*Princípios de Análise e Projeto de Sistemas com UML*), Wazlawick (*Análise e Projeto de Sistemas de Informação Orientados a Objetos*), Fowler (*UML Essencial*) e Booch, Rumbaugh e Jacobson (*UML — Guia do Usuário*).

## Projeto relacionado

O banco de dados relacional derivado deste modelo de análise foi desenvolvido no semestre seguinte, na disciplina de Modelagem e Implementação de Banco de Dados com SQL.

## Equipe

- Ágatha Santos de Souza
- André Barçante de Carvalho
- Andrey Lucas Castilho Manhães
- Daniel Rios de Mello de Castro
- Letícia dos Reis Prado

**Orientador:** Cláudio Ribeiro da Silva · **Co-orientador:** Flavio Maggessi Viola
