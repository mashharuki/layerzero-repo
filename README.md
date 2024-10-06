# layerzero-repo

LayerZero を学ぶためのサンプルリポジトリです。

## LayerZero とは何か？

異なるブロックチェーン間でコントラクトのメッセージのやり取りを可能にするクロスチェーンプロトコル

## クイックスタート

Use LayerZero's Contract Standards to easily start sending arbtirary data, tokens, and external calls using the protocol:

- Omnichain Application (OApp):  
  the base contract standard for omnichain messaging and configuration.

- Omnichain Fungible Token (OFT):  
  an extension of OApp built for handling and supporting omnichain ERC20 transfers.

- Omnichain Non-Fungible Token (ONFT):  
  an extension built for handling and supporting omnichain ERC721 transfers.

## テンプレプロジェクト生成コマンド

```bash
npx create-lz-oapp@latest
```

## トークンを送金する仕組み

LayerZero を使って異なるブロックチェーンネットワークにトークンを転送するには、次の 3 つの方法があります。

LayerZero のコントラクト標準を使用して、自分のオムニチェーントークンを作成する。
メッセージの実行オプションの一部としてネイティブガストークンを送信する。

LayerZero 上に構築されたネイティブブリッジを利用する（例：Stargate）。
オムニチェーントークンの作成

オムニチェーン・ファンジブル・トークン（OFT）標準およびオムニチェーン・ノンファンジブル・トークン（ONFT）標準は、複数のチェーン上に存在するトークンを作成するのに最適です。

これらの標準は、資産のラッピングや中間チェーンを必要とせず、トークンを複数のブロックチェーン間で転送でき、保有者に一貫性と相互運用性を提供します。

新しいトークンを作成する場合は、OFT または ONFT を継承します。
既存のトークンを使用する場合は、OFTAdapter または ONFTAdapter を使用します。
OFT や ONFT を使用してトークンを作成するには、トークンが存在する、または存在する予定の各チェーンに標準コントラクトをデプロイする必要があります。

詳細は、OFT クイックスタートおよび ONFT クイックスタートを参照してください。

少量のネイティブガスの送信
宛先アプリケーションのロジックによっては、宛先チェーンの取引手数料や、新しいブロックチェーンへのユーザーのオンボーディングを支援するために、少量のネイティブガストークンを転送したい場合があります。

LayerZero のメッセージ実行オプションを使用すると、クロスチェーンコールの一部として、または宛先チェーン上の特定のアドレスに少量のネイティブガスを送信できます。

lzReceive: 宛先の EndpointV2.lzReceive コールの一部として gasLimit および/または msg.value を送信します。
lzCompose: 宛先の EndpointV2.lzCompose コールの一部として gasLimit および/または msg.value を送信します。
lzNativeDrop: 特定の\_receiver アドレスにネイティブガスを wei 単位で指定量送信します。
これらのガス量は、アプリケーション内の EndpointV2.send の呼び出し元によってソースチェーンで支払われ、ユーザーのガス管理が簡略化されます。

詳細は「Transaction Pricing」を参照してください。

ネイティブ資産の移動（例：wETH、USDC、USDT）
すでに他のコントラクトオーナーによってデプロイされたネイティブ資産を移動するためには、次の 2 つの方法があります。

オプション 1: LayerZero 上に構築されたプロトコルまたはネイティブブリッジ
LayerZero 上に構築されたプロトコル、分散型取引所（DEX）、またはネイティブ資産ブリッジ（例：Stargate）を利用して、チェーン間でネイティブ資産を転送します。

機能性: Stargate や同様のプラットフォームは、資産プールの作成を処理し、複数のチェーン間でネイティブ資産の移動を簡単にします。
利点: このオプションにより、OFT 標準を直接デプロイする必要がなく、既存の流動性とスマートコントラクトとの互換性を活用できます。
スマートコントラクト内でクロスチェーン資産を転送・交換する方法については、「Stargate Docs」を参照してください。

オプション 2: ラップド資産ブリッジ
自分のブロックチェーンを運営している場合、LayerZero Labs に連絡して、自分のネットワーク上に LayerZero Endpoint コントラクトをデプロイすることができます。これにより、既存の資産を簡単に移動できるラップド資産ブリッジを作成することができます。

ラップド資産ブリッジ: このブリッジは、ソースチェーン上でトークンをロックし、OFT 標準を使用して宛先チェーン上で同等のトークンを発行します。
注意: このブリッジがチェーンから承認されない場合、この方法は推奨されません。新しいトークン標準（例：「yourUSDC」）を DeFi アプリケーションに受け入れてもらい、流動性を提供する必要があるためです。既存のトークンやチェーンから承認されたトークンは、より高い互換性と使いやすさを持っています。

### 参考情報

1. [LayerZero-Labs/solidity-examples](https://github.com/LayerZero-Labs/solidity-examples)
2. [【完全保存版】LayerZero の簡易テストを実行しよう！](https://note.com/standenglish/n/n28474e5d4eff)
3. [【完全保存版】LayerZero の「PingPong」コントラクトでチェーン間でメッセージを送ろう！](https://note.com/standenglish/n/n1bf4be024e11)
4. [【完全保存版】LayerZero でチェーン間のトークン移動を行おう！](https://note.com/standenglish/n/n5cbb1607a97e)
5. [LayerZero HP](https://layerzero.network/)
6. [ブロックチェーン相互運用性プロトコル「LayerZero（レイヤーゼロ）」とは](https://coinpost.jp/?p=439167)
7. [Endpoint TestnetAddresses](https://layerzero.gitbook.io/docs/technical-reference/testnet/testnet-addresses)
8. [GibHub - LayerZero-Labs](https://github.com/LayerZero-Labs)
9. [ドキュメント](https://docs.layerzero.network/v2/developers/evm/overview)
