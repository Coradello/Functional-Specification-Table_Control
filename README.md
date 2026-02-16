# Functional-Specification

Programa 1 – Consulta de Voos
Descrição
Criar um module pool que permita:


1.	Exibir em uma table control os dados de companhias aéreas (SCARR) e suas rotas de voo (SPFLI). Campos a serem exibidos na table control:
SCARR-CARRID (Companhia aérea)
SPFLI-CONNID (Conexão de voo)
SBOOK-FLDATE(Selecionar uma linha para cada data diferente)
SPFLI-COUNTRYFR 
SPFLI-CITYFROM               
SPFLI-AIRPFROM 
SPFLI-COUNTRYTO. 
SPFLI-CITYTO.
SPFLI-DEPTIME.  
SPFLI-ARRTIME.
2.	Permitir que o usuário selecione uma linha ou mais da table control
3.	Ter três botões de ação:
o	Exibir Reservas → abre um ALV com os dados de reservas da tabela SBOOK. Campos a serem exibidos no ALV:
SBOOK-CARRID 
SBOOK-CONNID 
SBOOK-FLDATE       
SBOOK-BOOKID   
SBOOK-CUSTOMID
SBOOK-PASSNAME
o	Exportar CSV → gera um arquivo .csv, separado por ; com os dados da seleção da table control.
SCARR-CARRID
SPFLI-CONNID
SCARR-URL
SCUSTOM-ID
SCUSTOM-NAME        
SCUSTOM-FORM        
SCUSTOM-STREET      
SCUSTOM-POSTCODE   
SCUSTOM-CITY        
SCUSTOM-COUNTRY 
SCUSTOM-REGION 
SCUSTOM-TELEPHONE
SCUSTOM-EMAIL
o	Imprimir → gera um SmartForms contendo os dados da reserva. Abaixo segue o Layout do formulário e a especificação campos fixos e variáveis
 


Abaixo segue um exemplo de como deve ficar preenchido:
 
Requisitos técnicos
•	Telas:
o	Tela principal (dynpro) com:
	Ao informar a compania aérea e dar enter a table control deve ser preenchida
	Table control.
	Botões: "Exibir Reservas", "Exportar CSV", "Imprimir".
•	Fluxo:
o	Seleção da linha → clique no botão → ação correspondente.
•	ALV:
o	Usar CL_SALV_TABLE ou REUSE_ALV_GRID_DISPLAY.
•	CSV:
o	Exportação usando GUI_DOWNLOAD.
•	SmartForms:
o	Layout simples: cabeçalho com companhia aérea, rota e tabela com reservas.

Transação
•	Criar uma transação Z associada ao programa do module pool.

________________________________________
🟠 Programa 2 – Importação de Arquivo CSV
Descrição
Criar um programa ABAP Report que:
1.	Leia um arquivo .CSV do desktop, gerado no programa do item 1.
2.	Grave os dados em uma tabela Z criada pelos alunos.
3.	A tabela Z deve ter gerador de manutenção (SM30) e uma transação associada para manutenção manual dos registros.
Estrutura sugerida para tabela Z
Campos:
•	MANDT (cliente)
•	CARRID	mesmo elemento de dados de    SCARR-CARRID
•	CONNID	mesmo elemento de dados de    SPFLI-CONNID
•	URL		mesmo elemento de dados de    SCARR-URL
•	ID		mesmo elemento de dados de    SCUSTOM-ID
•	NAME       	mesmo elemento de dados de    SCUSTOM-NAME     
•	FORM       	mesmo elemento de dados de    SCUSTOM-FORM     
•	STREET     	mesmo elemento de dados de    SCUSTOM-STREET   
•	POSTCODE   	mesmo elemento de dados de    SCUSTOM-POSTCODE 
•	CITY       	mesmo elemento de dados de    SCUSTOM-CITY     
•	COUNTRY 	mesmo elemento de dados de    SCUSTOM-COUNTRY 
•	REGION 	mesmo elemento de dados de    SCUSTOM-REGION 
•	TELEPHONE	mesmo elemento de dados de    SCUSTOM-TELEPHONE
•	EMAIL		mesmo elemento de dados de    SCUSTOM-EMAIL



Requisitos técnicos
•	Leitura do CSV via GUI_UPLOAD ou CL_GUI_FRONTEND_SERVICES=>GUI_UPLOAD.
•	Parser linha a linha, split por ;.
•	INSERT em ZVOOS_CARGA.
•	Commit após gravação.
Transação
•	Criar uma transação Z associada ao programa de importação.
•	Criar também a transação SM30 gerada para manutenção da tabela Z.
________________________________________
🔑 O que será avaliado
•	Correção da lógica (seleção, exibição, exportação, gravação).
•	Uso correto de module pool com table control.
•	Criação e uso de ALV.
•	Implementação de SmartForms.
•	Manipulação de arquivos CSV (exportar/importar).
•	Criação e manutenção de tabelas Z.
•	Organização do código e uso de boas práticas (MOVE-CORRESPONDING, CHECK, LOOP, etc.).
________________________________________
🎯 Dicas para os estagiários
•	Quebrem o exercício em partes menores e testem passo a passo.
•	Revisem os conceitos de flow logic (PBO/PAI) no module pool.
•	Lembrem-se de usar SORT/READ TABLE BINARY SEARCH quando compararem dados em tabelas internas.
•	No SmartForms, foquem em algo simples (não precisa ser layout sofisticado).

