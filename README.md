# Você ainda faz testes manuais no ServiceNow?

Se você é desenvolvedor ou administrador ServiceNow, sabe que cada nova atualização ou customização traz aquele frio na barriga: "Será que quebrei algo que já estava funcionando?"
O Automated Test Framework (ATF) é a ferramenta nativa que resolve esse problema, garantindo a qualidade das suas entregas e economizando horas de trabalho manual.
Aqui estão os pontos fundamentais que você precisa saber para dominar o ATF:

✅O que é o ATF? É o framework oficial para criar e executar testes automatizados que validam suas aplicações e configurações após upgrades ou mudanças. 

✅Elementos Chave:
•	Test Cases & Steps: Ações individuais como criar registros ou validar visibilidade de campos.
•	Test Suites: Agrupamentos de testes para execuções em massa.
•	Test Runner: A interface que executa visualmente os passos no navegador.

✅O Poder do Rollback: O melhor do ATF? Ele não "suja" sua instância. Após o teste, o sistema faz um rollback automático de todos os dados criados (usuários, incidentes etc.). 

⚠️ Dica de Ouro: Nunca execute testes de ATF em instâncias de Produção. O foco deve ser sempre em Dev e Test!

 
## Construção de um Guia Prático: Automação de Testes (ATF) na ServiceNow

Para quem quer começar a automatizar, aqui está o fluxo real de um teste de criação de incidente:

1. Configuração Inicial Criamos o teste "Validação criação de incidente". Note que o ServiceNow avisa se a execução de testes está habilitada na instância — um detalhe importante de governança!

 <img width="884" height="266" alt="image" src="https://github.com/user-attachments/assets/f26f5a25-933b-439c-9583-b4b970216771" />

FIGURA 1: Definindo o objetivo — validar se um usuário ITIL consegue criar incidentes sem erros.

2. Definindo a Lógica - Test Steps. Estruturamos 6 passos:
<img width="884" height="331" alt="image" src="https://github.com/user-attachments/assets/e9b0bfd2-7ba1-427d-a044-bbbdc984079f" />
 
FIGURA 2: Estruturação de 6 passos, desde a criação do usuário fictício até a validação de campos obrigatórios.

•	Criar um usuário com role itil (Alan Sousa).

•	Abrir o formulário de incidente.

•	Preencher os campos (Short description e Caller).

•	Submeter o formulário.

•	Reabrir o registro criado e validar se os estados dos campos (obrigatórios/visíveis) estão corretos.

3. O Test Runner FIGURA 3 a 5 O Client Test Runner assume o controle do navegador e preenche o formulário automaticamente. Uma nova janela abre e você vê o sistema operando sozinho:

<img width="884" height="326" alt="image" src="https://github.com/user-attachments/assets/81b26e93-b782-48c3-8aea-9225280f2040" />
 
<img width="884" height="292" alt="image" src="https://github.com/user-attachments/assets/f400479b-e4d0-4582-9e09-28733ee6366b" />
 
FIGURA 4: O sistema aguarda a conexão.

<img width="884" height="419" alt="image" src="https://github.com/user-attachments/assets/29de93e6-e853-4429-9214-affcbf7acb50" />
 
FIGURA 5: Vemos o formulário sendo preenchido automaticamente com os dados do Alan Sousa em tempo real.

4. Validação e Checkpoint Após submeter, o ATF reabre o incidente (INC0010002) para garantir que tudo o que o desenvolvedor configurou (regras de negócio, UI Policies) está se comportando como deveria.

<img width="884" height="347" alt="image" src="https://github.com/user-attachments/assets/ea580b25-9210-4bcc-9a99-a6da558beb7b" />
 
FIGURA 6: O sistema reabre o registro criado para checar se as UI Policies e regras de negócio estão ativas.

5. O Veredito e Rollback Teste finalizado com 100% de sucesso! O ponto alto aqui é o Rollback: o ServiceNow desfaz todas as alterações. O incidente criado e o usuário Alan Sousa são removidos automaticamente para não poluir a base de dados.

<img width="886" height="456" alt="image" src="https://github.com/user-attachments/assets/d186048d-af9e-4cf3-ac69-d38b306681fe" />
 
FIGURA 7: O teste passa com 100% de sucesso e o Rollback entra em ação, apagando os dados de teste.

6. Relatório Detalhado FIGURA 8 O resultado entrega uma tabela detalhada com o tempo de execução de cada passo. Transparência total para auditoria.

<img width="884" height="334" alt="image" src="https://github.com/user-attachments/assets/c4d9108a-9fd2-457f-a43b-bd22de37ca3a" />
 
FIGURA 8: Auditoria completa com o tempo de execução de cada etapa.

Links úteis: 
https://www.servicenow.com/br/products/automated-test-framework.html?state=seamless

https://youtu.be/bjCkgK0tahE

#ServiceNow #ATF #AutomatedTesting #DevOps #LowCode


