# Desafio Técnico - Procurador

## Descrição do problema

A intelivix está precisando de ajuda para capturar documentos jurídicos em formato PDF, extrair os números dos processos que estão nesse PDF e armazená-los em formato .CSV num bucket na AWS.

## Especificação dos dados
- Utilizar step function - Fluxo de trabalho que serve para orquestrar serviços da AWS. A ideia é usá-lo para disparar os lambdas que serão usados.
- Utilizar lambda function - É um serviço servless que lhe deixa rodar código (python nesse caso) sem precisar levantar um servidor. 
- Utilizar bucket no s3 - Serviço de armazenamento simples da AWS.
- Os pdfs devem ser capturados do seguinte link: https://consultasaj.tjam.jus.br/cdje
- Devem ser baixados 5 pdfs de quaisquer datas e o destino deles deve ficar da seguinte maneira: S3://teste-intelivix/artefatos/pdfs/<data_pdf>/<nome_do_arquivo>.pdf
- O destino do csv com os dados dos processos devem ficar no seguinte caminho: S3://teste-intelivix/artefatos/csvs/<nome_do_arquivo>.csv

## Requisitos

- Criar uma step function para orquestrar os lambdas que serão utilizados com argumento inicial da data do pdf para baixar.
- Criar lambda que vai pegar a data do pdf e baixar o pdf desejado e passar pro próximo lambda.
- Criar lambda que vai abrir o pdf, extrair via reger NPUs encontrados nele, jogar essas números num csv e salvar esse csv no S3.
- Criar um usuário extra para a pessoa avaliadora entrar na conta e executar o fluxo e ver artefatos.

## Critérios de avaliação
Os critérios de avaliação, em ordem de relevância:

1. Código legível, simples e claro;
2. Utilização da arquitetura da AWS;
3. Documentação clara de como executar fluxo;

Algumas observações:

 - Links úteis:
    - Stepfunction: https://docs.aws.amazon.com/pt_br/lambda/latest/dg/services-stepfunctions.html
    - Fluxo de trabalho integrando stepfunction + lambdas: https://aws.amazon.com/pt/getting-started/hands-on/create-a-serverless-workflow-step-functions-lambda/
    - NPU significa Numeração Processual Única com 20 dígitos que começou a ser adotado em 2010. O padrão na numeração é explicado aqui: https://tj-pe.jusbrasil.com.br/noticias/2049972/judiciario-adota-novo-sistema-de-numeracao-processual 
- Mock de diagrama de como deveria ser o fluxo do step function:

![diagrama_stepfunction](https://user-images.githubusercontent.com/8882260/128194034-1318fc89-7a9b-4832-acf0-0c324505bd0a.png)
