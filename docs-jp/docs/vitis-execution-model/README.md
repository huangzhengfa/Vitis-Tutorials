<table>
 <tr>
   <td align="center"><img src="https://www.xilinx.com/content/dam/xilinx/imgs/press/media-kits/corporate/xilinx-logo.png" width="30%"/><h1>2019.2 Vitis™ アプリケーション アクセラレーション開発フローのチュートリアル</h1><a href="https://github.com/Xilinx/SDAccel-Tutorials/branches/all">SDAccel™ 開発環境 2019.1 チュートリアルを参照</a></td>
 </tr>
 <tr>
 <td align="center"><h1>入門コース</h1>
 </td>
 </tr>
</table>

# FPGA アクセラレーション アプリケーションの実行モデル

## 概要

Vitis™ コア開発キットのアクセラレーション アプリケーションは、ソフトウェア プログラムとハードウェア アクセラレーションされたカーネルを含む FPGA バイナリの 2 つのコンポーネントで構成されます。これら 2 つのコンポーネント間の制御および通信は、ザイリンクス ランタイム ライブラリ (XRT) で管理されます。

* C/C++、および OpenCL™ のような API 呼び出しを使用して記述されたソフトウェア プログラムは x86 サーバーで実行されます。
* ハードウェア アクセラレーションされたカーネルは Alveo™ データセンター アクセラレータ カード上のザイリンクス FPGA デバイスで実行されます。

XRT で管理されるソフトウェア プログラム内の API 呼び出しにより、ホストとデバイス間でデータが転送され、カーネルが実行され、最適に同期されます。ホスト x86 サーバーおよびアクセラレータ カード間の通信には、PCIe® バス、またはエンベデッド プラットフォームの AXI バスが使用されます。データは、ソフトウェア プログラムから指定したカーネルに直接送信されるか、グローバル メモリ (ソフトウェアとカーネルの両方からアクセスされる共有メモリ空間) に含められます。

次の図は、このアクセラレーション ターゲット プラットフォームの一般的な構造を示しています。

![host\_fpga\_partition\_structure](images/host_fpga_partition_structure.png)

右側の FPGA ハードウェア プラットフォームにはハードウェアアクセラレーションされたカーネル、グローバル メモリとメモリ転送用の DMA が含まれます。カーネルには 1 つまたは複数のグローバル メモリ インターフェイスを含むことができ、プログラム可能です。

実行モデルでは、次が実行されます。

1. ホスト プログラムが、Alveo データセンター アクセラレータ カード上の PCIe インターフェイスまたはエンベデッド プラットフォームの AXI バスを介して、カーネルで必要なデータをグローバル メモリに書き込みます。
2. ホスト プログラムが、入力パラメーターを使用してカーネルを設定します。
3. ホスト プログラムが FPGA のカーネル関数の実行をトリガーします。
4. カーネルが、必要に応じてグローバル メモリからのデータを読み出しながら、計算を実行します。
5. カーネルがグローバル メモリにデータを書き込み、ホストにタスクが終了したことを通知します。
6. ホスト プログラムは、グローバル メモリからホスト メモリにデータを転送するか、別のカーネルにデータを送信して処理します。

## 次のステップ

コア開発キットをインストールして設定し、Vitis ツールを使用してホスト プログラムとハードウェア カーネルをビルドします。Alveo データセンター アクセラレータ カードを開発システムまたは運用システムにインストールして設定します。

[詳細を読む](../../docs/alveo-getting-started/README.md) </br>

<hr/>
<p align= center><b><a href="../../README.md">メイン ページに戻る</a> &mdash; <a href="../../docs/vitis-getting-started/README.md">入門コースの初めに戻る</a></b></p></br><p align="center"><sup>Copyright&copy; 2019 Xilinx</sup></p>

この資料は表記のバージョンの英語版を翻訳したもので、内容に相違が生じる場合には原文を優先します。資料によっては英語版の更新に対応していないものがあります。日本語版は参考用としてご使用の上、最新情報につきましては、必ず最新英語版をご参照ください。

