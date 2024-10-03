# Laravel Breeze - Next.js 版本 ▲

## 介紹

此資料庫實作了 [Laravel Breeze](https://laravel.com/docs/starter-kits) 應用程式與認證起始套件的前端，並使用 Next.js [Next.js](https://nextjs.org) 框架。所有的認證樣板程式碼都已經為你撰寫完畢，透過 Laravel Sanctum [Laravel Sanctum](https://laravel.com/docs/sanctum) 提供支援，讓你可以快速將美麗的 Next.js 前端與強大的 Laravel 後端結合。

來源: [breeze-next](https://github.com/laravel/breeze-next) | 當前版本 "next": "^14.2.10", "laravel/framework": "^11.9"

## 官方文件

### 安裝

1. 建立Laravel後端：創建一個與 Next.js 相容的 Laravel 後端，使用 [fresh Laravel application](https://laravel.com/docs/installation) 安裝 Laravel 以及 Breeze：

```bash
# 建立laravel後端 with breeze api
laravel new api
```

2. 運行Laravel後端：確認應用程式的 `APP_URL` 和 `FRONTEND_URL` 環境變數已分別設定為 `http://localhost:8000` 和 `http://localhost:3000`。

在定義好相關環境變數後，你可以使用 `serve` Artisan 命令來啟動 Laravel 應用程式：

```bash
# 啟動應用程式...
php artisan serve
```

3. 建立Next前端：克隆這個資料庫 [breeze-next](https://github.com/laravel/breeze-next)，並使用 npm i 安裝相依套件。然後，將 .env.example 複製為 .env.local 並提供後端的 URL：

```
NEXT_PUBLIC_BACKEND_URL=http://localhost:8000
```

4. 運行Next前端：透過 npm run dev 來執行應用程式。應用程式將可透過 http://localhost:3000 存取：

```bash
npm run dev
```

> 注意：我們建議在本地開發環境中使用 `localhost` 來避免 CORS（跨來源資源共享）「相同來源」的問題。

### 認證 Hook

此 Next.js 應用程式包含一個自訂的 `useAuth` React hook，旨在將所有認證邏輯從頁面中抽象出來。此外，此 hook 還可以用來存取目前認證的使用者：

```js
const ExamplePage = () => {
    const { logout, user } = useAuth({ middleware: 'auth' })

    return (
        <>
            <p>{user?.name}</p>

            <button onClick={logout}>Sign out</button>
        </>
    )
}

export default ExamplePage
```

> 注意：你將需要使用 [optional chaining](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining) （例如使用 user?.name 而非 user.name）來存取使用者物件的屬性，這是為了應對 Next.js 的初次伺服器端渲染。

😊
