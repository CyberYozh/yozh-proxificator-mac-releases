# YozhProxificator para Mac

[English](README.md) · [Русский](README.ru.md) · [Українська](README.uk.md) · [Español](README.es.md) · Português · [Tiếng Việt](README.vi.md) · [Bahasa Indonesia](README.id.md) · [简体中文](README.zh-Hans.md) · [繁體中文](README.zh-Hant.md)

O tráfego do seu Mac por proxies: o Mac inteiro ou só os aplicativos que você escolher.

- **O Mac inteiro.** “Todo o tráfego” envia pelo proxy tudo o que o Mac envia, até os aplicativos que ignoram os ajustes de proxy.
- **Cada aplicativo do seu jeito.** Envie um aplicativo pelo próprio proxy ou cadeia, diretamente ou sem rede nenhuma, e faça o mesmo com listas inteiras de sites.
- **Sem vazamentos.** O desligamento de emergência não deixa um aplicativo com regra acessar a rede senão pelo proxy dele, mesmo quando você está desconectado. Em “Todo o tráfego”, o próprio proxy descobre os endereços dos sites, então um teste de vazamento de DNS mostra o lado do proxy.
- **Qualquer proxy.** HTTP, HTTPS e SOCKS5; links e assinaturas de VLESS, VMess, Trojan, Shadowsocks e Hysteria2; cadeias de dois proxies.
- **Verificação com um clique.** “Verificar” mostra se um proxy funciona, com que rapidez ele conecta e em que país ele sai.
- **Para clientes da CyberYozh.** Seus proxies comprados são carregados pela chave de API. O gerador cria proxies de rotação por país, cidade e provedor, e pode dar a eles um SO escolhido e a impressão digital TLS de um navegador. Os proxies móveis trocam de IP com um clique.

## Baixar

Este link sempre leva à versão mais recente:
**[YozhProxificator.dmg](https://github.com/CyberYozh/yozh-proxificator-mac-releases/releases/latest/download/YozhProxificator.dmg)**

Requisitos: um Mac com Apple silicon, macOS 15 ou posterior.

O download é uma imagem de disco. Ela contém o aplicativo e um atalho para a pasta Aplicativos, nada mais. Abra a
imagem e arraste o YozhProxificator para Aplicativos, ou abra o aplicativo a partir da imagem: ele se oferece para se
mover para lá. O aplicativo se atualiza a partir deste repositório; as atualizações são assinadas, e as verificações
automáticas podem ser desativadas nos ajustes dele.

## Verifique o que você baixou

Cada versão pública, `vX.Y.Z`, tem um arquivo `SHA256SUMS` com o SHA-256 dos seus arquivos. Baixe-o na pasta onde está a
imagem e execute, no Terminal, nessa pasta:

    shasum -a 256 -c SHA256SUMS --ignore-missing

Uma versão de teste na versão `acceptance` tem, em vez disso, um arquivo `SHA256SUMS-X.Y.Z` próprio: baixe esse ao lado
da imagem e coloque o nome dele no comando.

A imagem é assinada com Developer ID e notarizada pela Apple. Coloque o nome do seu arquivo no lugar de
`YozhProxificator.dmg`:

    spctl -a -t open --context context:primary-signature -v YozhProxificator.dmg

Ele responde `accepted` e `source=Notarized Developer ID`.

## Código-fonte

O YozhProxificator é software livre sob a GNU GPL v3, sem garantia. Cada versão pública `vX.Y.Z` e cada versão de teste
na versão `acceptance` traz o código-fonte completo do que distribui:

- `yozh-proxificator-mac-X.Y.Z-source.tar.gz` — o aplicativo, o componente do sistema dele e os scripts de build;
- `yozh-xray-<commit>-source.tar.gz` — o motor de proxy, um fork do Xray-core, no commit que o build fixa (`<commit>` são
  os primeiros doze caracteres desse commit);
- `sparkle-<version>-source.tar.gz` — o framework de atualização.

## Como desinstalar

1. Em **Ajustes → Todo o tráfego** do aplicativo, clique em **Remover componente**.
2. Mova o aplicativo para a Lixeira.
3. Se os programas ficarem sem rede, abra o **Yozh Unblock** a partir de Aplicativos. Se a rede sumir depois da remoção,
   execute `sudo /Library/PrivilegedHelperTools/com.cyberyozh.proxyficator/yozh-helper restore` no Terminal.

## Os feeds de atualização

O aplicativo lê um feed — uma lista de versões, com as imagens e as notas para as quais elas apontam — para saber se
existe uma versão mais nova. Há dois feeds, cada um em uma versão própria:

- `acceptance` é uma pré-versão com as versões de teste internas (0.9.x) e o feed delas, não para uso geral. Cada
  versão de teste vem com seus arquivos de código-fonte e o próprio `SHA256SUMS-X.Y.Z`; um arquivo do motor ou do
  framework que várias versões compartilham é guardado uma só vez. As versões de teste leem este feed, e a 1.0.0 também
  é publicada nele, então elas passam para o feed público com ela.
- `updates` é o feed das versões públicas. Ele é para o aplicativo, não para baixar; o código-fonte de cada versão dele
  está na versão `vX.Y.Z` correspondente.
