# sal1-notes
Private notes for CyberSecurity101 / SOC Lv1 / SAL1

1. 目的・構成・更新ルール

```md
# sal1-notes 🇯🇵

このリポジトリは **TryHackMe** の学習パス  
- **Cyber Security 101 (CS101)**  
- **SOC Level 1**  
- **Security Analyst Level 1 (SAL1)**  

で作成したチートシート & ラボ手順書をモジュール別に保存する “私的まとめノート” です。

```

```
## 📁 ディレクトリ構成

sal1-notes/
├─ CS101/      # Cyber Security 101 のメモ
├─ SOC\_Lv1/   # SOC Level 1 のメモ
├─ SAL1/       # Security Analyst Lv1 のメモ
└─ assets/     # 画像や PDF
```

````
## 🔄 更新ルール
1. **動画／ラボ 1 本ごと** に 5-10 行の .md を追加  
2. 変更したら  
   ```bash
   git add .
   git commit -m "add CS101 Linux shell notes"
   git push
````

2. 空フォルダを残したいときは `.gitkeep` を置く

```

> *ポイント*  
> - 冒頭に目的を 1 行 → 構成を 1 行で書くと GitHub のトップページに抜粋が表示されます。  
> - 更新ルールは “自分用の To-Do” でもあるので、コマンド例を入れると迷いません。
::contentReference[oaicite:0]{index=0}
```

3. TL;DRとは
```
TL;DR は “Too Long; Didn’t Read” の省略形で、

「（本文が）長いので読まなかった」→ 要点だけ教えて！

というインターネット・スラングです。

チートシートや README では
まず最重要ポイントを一行でまとめる見出し として使われるのが一般的です。
```

