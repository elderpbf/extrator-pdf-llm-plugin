# Extrator PDF para LLM

Extrai o texto de PDFs no seu computador, inclusive páginas escaneadas (OCR), para o Claude ler,
resumir e analisar. Feito para peças, decisões e autos processuais.

## Como usar

Instale o Extrator PDF para LLM pela Microsoft Store
(https://apps.microsoft.com/detail/9P08Z6RD6SG6) e entre na sua conta. Depois, peça ao Claude algo
como "resuma o PDF C:\Processos\sentenca.pdf". O Claude chama o Extrator, que grava um .txt ao lado
do PDF e devolve o texto para a conversa.

No Claude Desktop, adicione a pasta do processo pelo "+" ao lado da caixa de mensagem e peça ao
Claude pelo nome do arquivo. Um PDF arrastado ou anexado à conversa vai para o Claude, não fica no
seu computador, e por isso o Extrator não o alcança.

Funciona no Claude Code e nas sessões do Claude Desktop que rodam no seu computador.

## O que o plugin executa

O servidor MCP do plugin é o próprio Extrator PDF para LLM instalado pela Microsoft Store, iniciado
pelo nome fixo que o app registra no Windows: `%LOCALAPPDATA%\Microsoft\WindowsApps\extrator-pdf-llm.exe`,
com o argumento `--mcp`. O plugin não traz o programa dentro dele porque a extração depende da conta
do usuário no app, do motor de OCR que vem com ele e das atualizações da Store. Se o app não estiver
instalado, o servidor não inicia e o Claude indica onde baixá-lo.

O servidor oferece uma ferramenta, `extract_pdf`: recebe o caminho completo de um PDF, devolve o texto
e grava um .txt na pasta do próprio PDF. Ele recusa gravar fora dessa pasta e só substitui o PDF
original quando o usuário pede isso expressamente.

## Dados

A extração e o OCR rodam na sua máquina. O plugin não envia o PDF a nenhum servidor: só o texto
extraído entra na conversa com o Claude, como qualquer texto que você colasse nela.
