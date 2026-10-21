# F3F Energy CRM

CRM operacional da F3F Energy para clientes de energia solar, redes de distribuição, subestações, geração distribuída (GD), Mercado Livre de Energia e eficiência energética.

É um único arquivo (`index.html`). Não precisa de servidor nem de instalação: abra o arquivo no navegador (Chrome, Edge ou Firefox).

## Como usar

1. Abra `f3f-crm/index.html` no navegador.
2. O CRM abre com **dados de demonstração** (clientes fictícios da Serra Catarinense) para você conhecer as telas.
3. Quando quiser usar de verdade: **Backup → Apagar todos os dados**. As configurações e os modelos de mensagem são mantidos.
4. Preencha **Configurações** com os dados da empresa (CNPJ, CREA, telefone) e as premissas do dimensionamento solar.

Os dados ficam salvos no armazenamento local do navegador. Faça **Backup → Exportar** com frequência. O arquivo JSON gerado restaura tudo em outro computador.

## Fluxo

```
Captação → WhatsApp → Funil → Visita técnica → Orçamento → Aprovação → Projeto + Parcelas
```

| Tela | O que faz |
|---|---|
| Dashboard | Leads, propostas abertas, projetos ativos, kWp em execução, recebido no mês, parcelas e tarefas vencidas, alertas e pipeline por serviço |
| Captação | Contatos frios, importação de planilha CSV, atalho de busca no Google Maps, conversão em lead ou parceiro |
| WhatsApp | Fila de envio com modelos e variáveis (`{{nome_empresa}}`, `{{cidade}}`...). Cada envio abre o WhatsApp com o texto pronto e agenda o retorno |
| Agendas | Calendário mensal de visitas técnicas, vistorias, comissionamentos e reuniões. Exporta `.ics` para o Google Agenda |
| Leads e clientes | Dados da unidade consumidora: distribuidora, UC, grupo/modalidade tarifária, tensão, consumo, conta, demanda contratada e fator de potência |
| Parceiros | Integradores, distribuidores, comercializadoras, construtoras e bancos, com comissão e último contato |
| Funil comercial | Kanban arrastável: Novo → Contato → Qualificado → Visita → Proposta → Negociação → Fechado/Perdido |
| Reprospecção | Orçamentos parados, leads sem retorno, contatos sem resposta, parceiros esquecidos, clientes antigos e perdidos |
| Orçamentos | Itens, desconto, entrada e parcelas. Calcula o sistema fotovoltaico (kWp, módulos, inversor, geração, economia e payback), mostra a proposta formatada e envia pelo WhatsApp |
| Pagamentos | Parcelas geradas na aprovação, com status pago, pendente ou atrasado e lembrete pelo WhatsApp |
| Projetos | Criados ao aprovar o orçamento, já com as etapas do serviço como tarefas (parecer de acesso, homologação, vistoria, migração CCEE...) |
| Tarefas | Prazo, prioridade e peso no progresso do projeto, automático ou manual |
| Relatórios | Fluxo de recebimentos, funil acumulado, propostas por serviço, origem dos leads, kWp contratado e CO₂ evitado |

## Etapas-padrão por serviço

- **Energia solar:** visita técnica, projeto e ART, parecer de acesso, aprovação da concessionária, compra de equipamentos, instalação, vistoria/troca do medidor, comissionamento.
- **Redes de distribuição:** topografia, projeto MT/BT, aprovação, licenças, execução, energização, as-built.
- **Subestações:** levantamento de cargas, projeto, estudo de proteção e seletividade, aprovação, montagem, ensaios e comissionamento, ligação.
- **Geração distribuída:** análise das UCs, dimensionamento e modelo de compensação, parecer de acesso, licenciamento, construção, conexão, rateio de créditos.
- **Mercado Livre:** análise de faturas, viabilidade ACL × cativo, denúncia do contrato, comercializadora varejista, SMF e CCEE, migração, gestão mensal.
- **Eficiência energética:** diagnóstico, medição de qualidade de energia, relatório de oportunidades, correção de fator de potência, retrofit, M&V.

## Premissas do cálculo solar

`kWp = consumo ÷ (HSP × 30 × PR)`, arredondado para cima em número inteiro de módulos. A economia considera a energia compensada × tarifa × (1 − fio B). Os valores são estimativas comerciais; o dimensionamento final depende da visita técnica e do projeto executivo. Todas as premissas são editáveis em **Configurações**.

## Limitações desta versão

- Os dados ficam em um navegador por vez. Para várias pessoas usarem ao mesmo tempo, o próximo passo é um banco de dados online (por exemplo, Supabase) com login.
- O envio pelo WhatsApp é assistido: o CRM abre a conversa com o texto pronto e você confirma o envio. Não há disparo automático.
- A busca no Google Maps abre em outra aba; os contatos encontrados entram por CSV ou cadastro manual.
