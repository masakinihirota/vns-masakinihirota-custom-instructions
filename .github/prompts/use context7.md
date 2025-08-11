# use context7をプロンプトにつけて質問します。

## 使用例
React 19の新機能Suspenseの使い方を教えてください。use context7


## 回答

React 19 の新機能である `Suspense` は、非同期データの読み込み中にフォールバック UI を表示するために使用されます。以下に、サーバーコンポーネントとクライアントコンポーネントでの使用例を示します。Next.js の App Router 構造に従い、TypeScript で記述します。

---

### サーバーコンポーネントでの使用例

```tsx
import React, { Suspense } from 'react'

// 非同期データ取得関数
async function fetchData(): Promise<string> {
  return new Promise((resolve) => setTimeout(() => resolve('データが読み込まれました！'), 2000))
}

// サーバーコンポーネント
async function DataComponent() {
  const data = await fetchData()
  return <div>{data}</div>
}

export default function Page() {
  return (
    <div>
      <h1>サーバーコンポーネントでの Suspense 使用例</h1>
      <Suspense fallback={<div>読み込み中...</div>}>
        {/* サーバーコンポーネントをラップ */}
        <DataComponent />
      </Suspense>
    </div>
  )
}
```

---

### クライアントコンポーネントでの使用例

```tsx
'use client'

import React, { Suspense, useState, useEffect } from 'react'

// 非同期データ取得フック
function useFetchData(): string | null {
  const [data, setData] = useState<string | null>(null)

  useEffect(() => {
    const fetchData = async () => {
      const result = await new Promise<string>((resolve) =>
        setTimeout(() => resolve('クライアントデータが読み込まれました！'), 2000)
      )
      setData(result)
    }
    fetchData()
  }, [])

  if (!data) {
    throw new Promise((resolve) => setTimeout(resolve, 2000)) // Suspense による待機
  }

  return data
}

// クライアントコンポーネント
function DataComponent() {
  const data = useFetchData()
  return <div>{data}</div>
}

export default function Page() {
  return (
    <div>
      <h1>クライアントコンポーネントでの Suspense 使用例</h1>
      <Suspense fallback={<div>読み込み中...</div>}>
        {/* クライアントコンポーネントをラップ */}
        <DataComponent />
      </Suspense>
    </div>
  )
}
```

---

### 解説

1. **サーバーコンポーネント**:
   - `Suspense` を使用して非同期データ取得中にフォールバック UI を表示します。
   - サーバーコンポーネントは `async` 関数として記述可能です。

2. **クライアントコンポーネント**:
   - `useEffect` と `useState` を組み合わせて非同期データを取得します。
   - データがまだ取得されていない場合、`throw` を使用して `Suspense` に制御を渡します。

3. **フォールバック UI**:
   - `Suspense` の `fallback` プロパティで、データ読み込み中に表示する UI を指定します。

これにより、非同期データの読み込み中でもスムーズなユーザー体験を提供できます。
