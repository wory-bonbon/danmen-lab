<p align="left"><img src="assets/icon_wory-bonbon.png" width="120" alt="danmen-lab logo"></p>

<p align="left">
  <a href="https://wory-bonbon.github.io/danmen-lab/">
    <img alt="Run Web" src="https://img.shields.io/badge/Run%20Web-OPEN-%23FF8AD9?style=for-the-badge&labelColor=2B2145" />
  </a>&nbsp;&nbsp;
  <a href="https://wory-bonbon.github.io/danmen-lab/3Dscan_measure_startup_guide_v1_7_5.html">
    <img alt="Guide" src="https://img.shields.io/badge/Guide-OPEN-%23B58CFF?style=for-the-badge&labelColor=2B2145" />
  </a>
</p>

# 断面研究所／danmen-lab — v1.7.5

3Dアバターや衣装から断面を抽出・計測するためのミニマルなウェブツールです。  
水平（床基準）および縦割りX/Z（中心基準）の断面を切り、周長・幅(U)・厚み(V)・2点距離を即座に表示します。  
バージョン 1.7.5 では足底自動検出やログに3Dラインを記録する機能、任意方向への断面、単位選択など多数の機能強化を行いました。

[![v1.7.4 デモ動画](https://img.youtube.com/vi/B5_mohahV7w/maxresdefault.jpg)](https://youtu.be/B5_mohahV7w)

> ※ 上記は旧バージョン v1.7.4 のデモ動画です

---

## 📘 ドキュメントリンク

| リンク | 説明 |
|--------|------|
| ▶ [システム起動（Web）](https://wory-bonbon.github.io/danmen-lab/) | ブラウザで今すぐ起動 |
| 📘 [スタートアップガイド（Web）](https://wory-bonbon.github.io/danmen-lab/3Dscan_measure_startup_guide_v1_7_5.html) | 基本操作のガイド |
| 🗂 ガイドのHTML（リポジトリ内） | `./3Dscan_measure_startup_guide_v1_7_5.html` |

---

## 🚀 主な機能（v1.7.5）

| 機能 | 説明 |
|------|------|
| **断面抽出** | 水平断面（床基準）、縦割りX/Z（中心基準）に加え、任意の法線ベクトル（nx/ny/nz）とオフセットで任意面を定義可能 |
| **計測** | 周長・幅(U)・厚み(V)・2点間距離をリアルタイム表示。ShiftキーでU/V軸にロック |
| **ラベル操作** | ラベルはドラッグで移動可能、ダブルクリックで初期位置に戻る |
| **色設定** | メッシュのワイヤ色、断面ラインの通常色・選択色を即座に変更可能 |
| **ログ記録** | Capture は画面PNG保存＋計測ログ＋断面3Dラインを記録。ログパネルで各ラインの表示/非表示や削除、ライン太さの調整、CSV出力が可能 |
| **足底検出** | 足底自動検出、BBox底面、Y=0 の各ボタンで足底位置を設定。現在の断面位置を0mmとして採用することも可能 |
| **単位選択** | モデル単位（auto/mm/cm/m/inch）と表示単位を個別に指定可能 |
| **ビュー調整** | View ⟂（断面に正対）、Flip View（上下切替）、Up Axis（縦方向U/V切替）、Normal スナップ（法線を軸にスナップ）など |

---

## 📁 同梱ファイル

| ファイル | 説明 |
|----------|------|
| `index.html` | ツール本体 |
| `3Dscan_measure_startup_guide_v1_7_5.html` | スタートアップガイド（本体のUI解説） |
| `README.md` | このファイル |
| `LICENSE` / `NOTICE` / `THIRD_PARTY_NOTICES.md` | ライセンスとサードパーティ通知 |
| `assets/` | ロゴ画像などのリソース |

---

## 💻 使い方（ローカル）

オンライン利用を推奨します（three.js CDNを使用）。HTMLをブラウザで開くだけで動作します。オフライン運用時はJSライブラリを同梱してください。

---

## 📐 基本ワークフロー（水平断面）

| ステップ | 操作 |
|----------|------|
| 1 | モデルを読み込みます（glb/gltf/obj に対応） |
| 2 | **足底自動検出** で足底位置を決定（または **BBox底面** や **Y=0**）。必要に応じて現在の断面位置を **この位置を0mm** で固定 |
| 3 | **Height(mm)** に測定したい高さを入力し **適用** を押す |
| 4 | **View ⟂** で断面に正対し、必要に応じて **Caliper**（最大幅U・最大厚みVの自動計測）や **Solo View** を使用 |
| 5 | **Capture** で画面PNG＋ログ＋3Dラインを保存、または **Export @Scale** で固定スケールのPNGを出力 |

---

## 📐 縦割り断面（VX/VZ）

| ステップ | 操作 |
|----------|------|
| 1 | **Section** から **VX**（左右）または **VZ**（前後）を選択 |
| 2 | **中心から距離(mm)** にオフセット値を入力して **適用** を押す |
| 3 | **View ⟂** で断面に正対し、必要に応じて **Caliper** を使用 |
| 4 | **Capture** または **Export @Scale** で出力 |

---

## 🖼️ Export @Scale（縮尺を揃えた出力）

**mm/px**、**W(px)**、**H(px)**、**Margin(px)** を設定し **Export @Scale** を押すと、ズームやFOVに影響されない固定スケールのPNGを生成します。

### 推奨設定例

| 項目 | 値 |
|------|-----|
| mm/px | 1.00 |
| W×H | 1200×1200 |
| Margin | 80 |

案件間でこれらの値を固定すると、出力PNGの縮尺が一致します。断面が枠に収まらない場合は W/H を大きくするか mm/px の値を大きくしてください。

---

## 🖱️ クイックリファレンス

| 操作 | 動作 |
|------|------|
| **カメラ操作** | 左ドラッグ=回転、右ドラッグ=パン、ホイール=ズーム |
| **断面選択** | 断面ラインをクリック（選択色で表示） |
| **2点距離** | 断面上で2クリック。ShiftキーでU/V軸にロック |
| **ラベル** | ドラッグで移動、ダブルクリックでリセット |

---

## ⚖️ ライセンス

MIT License — 詳細は [LICENSE](./LICENSE) を参照

---

© 2025 断面研究所 (danmen‑lab) — v1.7.5
