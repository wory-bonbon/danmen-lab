# 3D Section Measure (proto v1.7)

3Dアバター／衣装の**断面抽出・計測**を、ブラウザだけで軽快に行う最小ツール。  
**水平（床基準）／縦割りX・Z（中心基準）**の断面を切り、**周長・幅(U)・厚み(V)・2点距離**を表示。  
比較用には **Export @Scale** で **オルソ＋固定スケール（mm/px）** のPNGを書き出せます（画面ズーム非依存）。

---

## できること（要点）
- 断面：水平（床＝BBox MinY）／縦割り（オブジェクト中心からの距離）
- 計測：周長・幅(U)・厚み(V)・2点距離（ShiftでU/Vにロック）
- ラベル：**ドラッグで位置調整**、**ダブルクリックで元位置に戻す**
- 色：メッシュの **Wire color**、断面 **Section line / Selected** を即変更（保存されます）
- ログ：**Capture** で「画面PNG保存＋計測ログ記録」、**CSVエクスポート**
- 比較：**Export @Scale**（オルソ固定スケール）で**縮尺の揃ったPNG**を出力（スケールバー付き）

---

## 同梱ファイル
- `3Dscan_measure_v1_7_scaled_export.html` … ツール本体  
- `3Dscan_measure_startup_guide_v1_7.html` … スタートアップガイド（ミニマルUI解説）

> 公開用には `index.html` にリネームすると GitHub Pages から直接起動できます。

---

## 使い方（ローカル）
- **オンライン推奨**（three.js CDNを使用）  
  そのままHTMLをダブルクリックでOK。オフライン運用時はCDNを同梱してください。

### 基本ワークフロー
1. モデル読込 → **Rotate X/Y/Z**（必要なら **Reset Rot**）
2. 断面タイプを選択：  
   - **Section: H** → **底面検出** → **Height(mm)** 入力 → **適用**  
   - **Section: VX / VZ** → **中心から距離(mm)** → **適用**
3. **View ⟂** → 必要なら **Caliper**（幅U・厚みV）／**Solo View**
4. 記録：**Capture**（画面PNG＋ログ）／比較用：**Export @Scale**

### Export @Scale（縮尺を揃える）
- `mm/px`（例：**1.00**）、`W/H(px)`（例：**1200×1200**）、`Margin(px)` を設定 → **Export @Scale**
- **画面ズームやFOVに非依存**。案件間で **mm/px** を固定すれば、**PNGの縮尺が完全一致**。
- 収まりきらない場合：`W/H` を増やすか、`mm/px` の数値を大きく（縮小方向）に。

---

## 画面操作（ショート解説）
- カメラ：左ドラッグ=回転／右ドラッグ=パン／ホイール=ズーム  
- 断面選択：断面ラインをクリック（選択色に変化）  
- 2点距離：選択断面上で2クリック（**Shift**でU/Vロック）  
- ラベル：ドラッグで移動、**ダブルクリック**でリセット

---

## 推奨プリセット（比較用）
- **mm/px:** `1.00`　**W×H:** `1200×1200`　**Margin:** `80`  
この数値を案件間で固定 → エクスポートPNGの縮尺が一致。左下スケールバーで目視確認。

---

## リポジトリ構成（提案）

3d-section-measure/
├─ index.html # 公開時は本体をリネーム（任意）
├─ 3Dscan_measure_v1_7_scaled_export.html
├─ 3Dscan_measure_startup_guide_v1_7.html
├─ README.md
├─ LICENSE
├─ NOTICE
└─ THIRD_PARTY_NOTICES.md
