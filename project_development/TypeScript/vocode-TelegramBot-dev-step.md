以下是使用 Visual Studio Code 環境下，開啟 TypeScript 專案開發 Telegram Bot 的步驟：

建立新的 TypeScript 專案：在 VS Code 中，按下 Ctrl+Shift+N 或選擇 "File" -> "New Project" 來建立一個新的專案。選擇 "TypeScript" 作為專案類型。

安裝 Telegram Bot 相關套件：在 VS Code 中，開啟終端機（Terminal），並執行以下指令安裝相關套件：
```
npm install --save node-telegram-bot-api
npm install --save-dev @types/node-telegram-bot-api typescript ts-node
```
建立 tsconfig.json 檔案：在專案資料夾中建立 tsconfig.json 檔案，並加入以下內容：
```json
{
    "compilerOptions": {
        "module": "commonjs",
        "esModuleInterop": true,
        "target": "es6",
        "moduleResolution": "node",
        "outDir": "dist",
        "baseUrl": ".",
        "sourceMap": true,
        "strict": true,
        "skipLibCheck": true,
        "forceConsistentCasingInFileNames": true
    },
    "include": [
        "src/**/*"
    ],
    "exclude": [
        "node_modules",
        "**/*.spec.ts"
    ]
}
```
這個檔案設定 `TypeScript` 編譯器的選項，包含編譯後的目標版本、是否使用 ES 模組系統等。

建立 `src` 資料夾及檔案：在專案資料夾中建立 `src` 的資料夾，並在其資料夾中建立 `index.ts` 的檔案。這個檔案是 Telegram Bot 的進入點。

撰寫 Telegram Bot 程式碼：在 `index.ts` 中撰寫 Telegram Bot 的程式碼。以下是一個簡單的範例：

```typescript
import TelegramBot from 'node-telegram-bot-api';

const bot = new TelegramBot('YOUR_TELEGRAM_BOT_TOKEN', { polling: true });

bot.on('message', (msg) => {
  const chatId = msg.chat.id;
  bot.sendMessage(chatId, 'Hello World!');
});
```
在這個程式碼中，我們使用 [node-telegram-bot-api](https://github.com/yagop/node-telegram-bot-api) 套件來開發 Telegram Bot，然後撰寫`訊息接收`與`訊息回傳`的工作。

執行 TypeScript 程式： 在 VS Code 中，開終端機（Terminal），並執行以下指令以啟動 TypeScript 編譯器：
```
tsc -w
```
這個指令會啟動 TypeScript 編譯器，以監控並即時編譯 TypeScript 程式碼。

接著，在另一個 Terminal 視窗中執行以下指令以啟動 Telegram Bot：
```
ts-node ./dist/index.js
```
這個指令會使用 ts-node 工具來執行 TypeScript 編譯後的 JavaScript 程式碼，啟動 Telegram Bot。

測試 Telegram Bot：在 Telegram 中與您的 Bot 對話，測試它是否能正常回傳訊息。
希望這些步驟能夠幫助您開始使用 Visual Studio Code 開發 TypeScript Telegram Bot！
