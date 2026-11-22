# 田中達也 ポートフォリオ（ソースコード閲覧用）

専門学校岡山情報ビジネス学院 ゲーム・VRクリエイター学科 ゲームクリエイターコース 3年
ゲームプログラマー志望です。

このリポジトリは、作品のソースコードを **ブラウザですぐに読んでいただくため** の場所です。
実行ファイル・プロジェクト一式・操作説明は、下の「作品一式」にまとめています。

| 用途 | リンク |
|---|---|
| 作品一式をダウンロード（実行ファイル・ソース・操作説明） | [Google ドライブ](https://drive.google.com/drive/folders/1kbPC88Cy7qecLfefJpyT7gSSDC_FWXRt?usp=sharing) |
| プレイ動画 | [ロケットにんげん](https://youtu.be/M52_JkC2Ve0) ／ [ラグドールシミュレーション](https://youtu.be/vFRE0bQyHMY) ／ [Knock Out](https://youtu.be/h6YeSHRonAI) ／ [ボスは二度戦う](https://www.youtube.com/watch?v=outBvxJZWHk) ／ [ShootingGame](https://youtu.be/Rb_ayFWECio) |
| 連絡先 | tatsuya.shuukatu@gmail.com |

---

## 作品とソースの場所

| 作品 | 内容 | 環境 | 人数 | ソースの場所 |
|---|---|---|---|---|
| ロケットにんげん | 大砲で人間を撃ち出して的を飛ばすゲーム。ラグドール物理を自作 | C++20 / DirectX 11 | 1人 | [RagDollSorce](RagDollSorce/)（.cpp）<br>[RagdollInclude](RagdollInclude/)（.h） |
| ShootingGame | 2D縦スクロールシューティング | C++20 / DxLib | 1人 | [SHOOTINGGAMESorce](SHOOTINGGAMESorce/)（.cpp）<br>[SHOOTINGGAMEInclude](SHOOTINGGAMEInclude/)（.h） |
| Knock Out | 1ボタンで技が出る初心者向け3D格闘ゲーム（東京ゲームショウ2025出展） | Unity / C# | 4人（リーダー） | [Script](Script/)（担当箇所のスクリプト） |

※ ラグドールシミュレーション、ボスは二度戦うのソースは、Google ドライブの各作品フォルダにあるプロジェクト一式に入っています。

---

## ロケットにんげん（C++ / DirectX 11・個人制作・約2か月半）

物理エンジン（剛体・ジョイント・衝突判定）を、外部ライブラリを使わずに自作しています。

**特に見ていただきたいコード**

| ファイル | 内容 |
|---|---|
| [Physics/PhysicsSystem.cpp](RagDollSorce/Physics/PhysicsSystem.cpp) | 1フレームを5回に分けて拘束を解く物理の更新処理 |
| [Ragdoll/BallJoint.cpp](RagDollSorce/Ragdoll/BallJoint.cpp) | 球関節。Swing-Twist分解による角度制限 |
| [Ragdoll/HingeJoint.cpp](RagDollSorce/Ragdoll/HingeJoint.cpp) | 蝶番関節（肘・膝） |
| [Ragdoll/Ragdoll.cpp](RagDollSorce/Ragdoll/Ragdoll.cpp) | モデルのボーンから剛体とジョイントを自動生成 |
| [Physics/Collision.cpp](RagDollSorce/Physics/Collision.cpp) | カプセル・箱・球の衝突判定と押し出し |
| [Physics/Octree.cpp](RagDollSorce/Physics/Octree.cpp) | Octreeによる空間分割（衝突判定の負荷削減） |
| [Factory/StageRoster.cpp](RagDollSorce/Factory/StageRoster.cpp) | ステージ・キャラクターをJSONから読み込むデータ駆動の仕組み |

---

## ShootingGame（C++ / DxLib・個人制作・1週間）

**特に見ていただきたいコード**

| ファイル | 内容 |
|---|---|
| [Base/StateMachine.h](SHOOTINGGAMEInclude/Base/StateMachine.h) | 汎用のステートマシン |
| [Character/BossStates.cpp](SHOOTINGGAMESorce/Character/BossStates.cpp) | 一定時間ごとに攻撃を切り替えるボス、HP4割で第二形態 |
| [Character/PlayerAttack.cpp](SHOOTINGGAMESorce/Character/PlayerAttack.cpp) | 武器の切り替えとヒートゲージ |
| [Base/ObjectPool.h](SHOOTINGGAMEInclude/Base/ObjectPool.h) | 弾のオブジェクトプール |

---

## Knock Out（Unity / C#・4人チーム・リーダー）

担当：プレイヤーの行動制御、入力デバイス管理、技のフレーム単位の管理

**特に見ていただきたいコード**

| ファイル | 内容 |
|---|---|
| [PlayerScript/MakePlayable.cs](Script/PlayerScript/MakePlayable.cs) | Playable APIを使ったフレーム単位のアニメーション制御 |
| [PlayerScript/AttackFrameController.cs](Script/PlayerScript/AttackFrameController.cs) | 技の発生・持続・硬直をフレームで管理 |
| [PlayerScript/ColliderManager.cs](Script/PlayerScript/ColliderManager.cs) | 当たり判定システム |
| [ManagerScript/ObjectPool.cs](Script/ManagerScript/ObjectPool.cs) | オブジェクトプール |
| [InputScriot/InputUserMakeManager.cs](Script/InputScriot/InputUserMakeManager.cs) | 複数コントローラーの接続とプレイヤーへの割り当て |
