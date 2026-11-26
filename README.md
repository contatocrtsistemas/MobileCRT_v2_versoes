# MobileCRT V2 — Atualizações

Repositório público de informações sobre as versões do **MobileCRT V2**, desenvolvido pela **CRT Sistemas**.

O MobileCRT V2 permite operar mesas, balcão, delivery, orçamentos e comandas, com integração ao Gerencial CRT. O acesso pode ser realizado pelo navegador, como PWA ou pelo aplicativo Android, conforme a configuração do servidor e do dispositivo.

## Conteúdo deste repositório

O arquivo [`versao.json`](./versao.json) informa a versão disponível, as novidades e o link público para baixar o instalador do servidor pelo MEGA.

Os fontes da aplicação são mantidos separadamente. A disponibilização deste manifesto não concede licença de uso ou de distribuição da aplicação.

## Como funciona a verificação

Nas instalações com o recurso de atualizações, o servidor consulta o manifesto a cada **6 horas** e na inicialização do Windows.

Quando encontra uma versão superior à instalada, a V2 exibe um aviso com as novidades e um link para o download no MEGA. O resultado e o horário da última consulta também podem ser conferidos em **Mais → Sobre**.

**O download e a instalação são manuais. O verificador não executa o instalador automaticamente.** Falhas na consulta de atualizações não interrompem a operação do sistema.

## Configurar o servidor

No próprio computador servidor, com a versão **2.1.17 ou posterior instalada**:

1. Abra o MobileCRT V2 e acesse **Mais → Configurações → Atualizações**.
2. Informe a URL do manifesto abaixo.
3. Salve as configurações.

```text
https://raw.githubusercontent.com/contatocrtsistemas/MobileCRT_v2_versoes/main/versao.json
```

Para consultar imediatamente, abra o **Agendador de Tarefas do Windows**, localize `MobileCRT-VerificarAtualizacoes` e selecione **Executar**. Depois confira o resultado em **Mais → Sobre** na V2.

Se a versão publicada for igual à instalada, o sistema informará que está atualizado. Deixar a URL em branco desativa a consulta.

## Baixar e instalar uma atualização

1. Consulte o aviso exibido na V2 ou o campo `download_url` do [`manifesto`](./versao.json).
2. Abra o link do MEGA e baixe o instalador correspondente à versão anunciada.
3. Faça o backup da base Firebird conforme o procedimento da empresa e programe uma pausa no atendimento.
4. Execute o instalador no **computador servidor**, como administrador, seguindo o guia de instalação que acompanha o pacote.
5. Ao concluir, confira o acesso ao sistema e a versão exibida em **Mais → Sobre**.

Durante a atualização, o serviço MobileCRT fica temporariamente indisponível. A atualização pelo instalador preserva a configuração da conexão, a CA e a base Firebird, conforme o procedimento descrito no guia.

## Publicar uma nova versão

Para os responsáveis pela distribuição:

1. Gere e valide o instalador da nova versão.
2. Envie o instalador ao MEGA e confira seu link público, incluindo a chave de acesso.
3. Atualize o arquivo `versao.json` na branch `main` com a versão, o link e as novidades.
4. Confirme a alteração e confira se a URL Raw retorna o JSON atualizado sem exigir autenticação.

Formato do manifesto:

```json
{
  "produto": "mobilecrt-v2",
  "versao": "2.1.17",
  "download_url": "https://mega.nz/file/IDENTIFICADOR#CHAVE",
  "novidades": [
    "Descrição das melhorias disponibilizadas nesta versão."
  ]
}
```

O JSON acima é um exemplo: substitua o endereço do MEGA antes de publicar. O campo `produto` deve permanecer como `mobilecrt-v2`. A versão deve corresponder ao instalador disponibilizado, no formato `X.Y.Z`, sem prefixo `v`.

O campo `novidades` aceita de **1 a 12 textos**, com até **600 caracteres por texto**. Utilize um link público HTTPS do MEGA com a chave incluída; endereços internos contendo `/fm/` não são aceitos.

Publique o instalador antes de anunciar a versão no manifesto. Mantenha o nome `versao.json` e seu caminho para preservar a URL configurada nos servidores.

Não inclua neste repositório senhas, tokens, arquivos de conexão, certificados com chaves privadas, dados de clientes ou cópias do banco de dados.

## Responsáveis

- **Empresa proprietária:** CRT Sistemas.
- **Desenvolvedor responsável:** Rafael Henrique Sales (Henrique Master).
- **Ano de desenvolvimento:** 2026.

© 2026 CRT Sistemas. Todos os direitos reservados.
