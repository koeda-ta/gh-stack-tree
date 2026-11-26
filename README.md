## gh stack-tree

指定したブランチを根元にして、その上に積まれた PR（stacked PR）の親子関係をツリーで表示する gh 拡張です。

```
feature/xxx/foundation
├─ ✓ #101 モデルを追加  [alice / merged 11-25]
├─   #102 API を追加  [bob / approved]
│  └─   #105 画面を追加  [bob / Draft]
└─   #103 通知メールを追加  [alice]
```

- ✓ はマージ済みの PR です
- 各行の角括弧の中に、作成者と状態（merged 月-日、Draft、approved）を表示します
- マージせずに閉じた PR は表示しません

### インストール

```
gh extension install koeda-ta/gh-stack-tree
```

jq が必要です。

### 使い方

```
gh stack-tree <ブランチ名>
```

ブランチ名を省略すると、今いるブランチを根元にします。

### 制限

直近 300 件の PR だけを対象にしています。それより古い PR がツリーの途中にあると、その PR より下の枝は表示されません。
