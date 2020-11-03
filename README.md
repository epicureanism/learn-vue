
## Require vs Import
| require                                                                                                                                                                                                                                                           | import                                                                                                                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 由 CommonJS 所支援 | ECMAScript 原生支援 |
| 執行到require 該行才進行載入<br><br>console.log("require module1");<br>const obj = require("./module2");<br>console.log(\`module2 = ${obj.module2}\`);<br>/\*\*\*\*\* Output \*\*\*\*\*/<br>require module1<br>require module2<br>module2 = require module2 | 一定會在開頭載入並預先執行，無論import 是否寫在檔案結尾<br><br>console.log("require module1");<br>import module2 from "./module2.js";<br>console.log(\`module2 = ${module2}\`);<br>/\*\*\*\*\* Output \*\*\*\*\*/<br>require module2<br>require module1<br>module2 = require module2 |
| 載入時是一行一行同步載入                                                                                                                                                                                                                                          | 載入時是非同步載入 (效能佳)                                                                                                                                                                                                                                          |
| Runtime 時期加載 (允許動態載入)<br><br><br>let name = a + b;<br>require('dep')                                                                                                                                                                                  | 編譯時期加載 (compile time loading) (變數無法動態加載)<br><br><br>let name = a + b;<br>//會噴error ↑<br>import { name } from dep |
| 執行整個js 檔，將結果export 為變數<br>let dep = require('dep')<br>dep.print();<br>console.log(dep.name);                                                                                                                                                          | 只載入欲載入的物件 (省資源)<br>import {print, name} from 'dep'<br>print();<br>console.log(dep.name);                                                                                                                                                                 |
