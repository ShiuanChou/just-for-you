# API-Design
## 第一次設計
## /user-account
### 個人帳戶資訊 
#### 單查
說明：

| General | 說明 | 
| --------------- | --- |
| Request Method  | GET |
| Request URL     | http://localhost:8080/user-account/profile |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |

**回傳：**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 | 
| ------ | ------- | --------- | ---- | --- |
| result | Boolean | API執行狀態 | true |    |
| errorCode | String | API執行異常代碼 | "" |    |
| message | String | API執行狀態說明 | "查詢成功" |    |
| data | Optional<Object> | 回傳資料 |  |    |
| userId | String | 使用者Google帳號 |  |    |
| userName | String | 使用者名稱 |  |    |
| userSex | String | 性別(男/女) |  | 後端需判斷 0:男/1:女 |
| department | String | 所屬科系/班級 |  |    |
| role | String | 角色/權限 |  | 對應codelist表role的desc |
| creatTime | String | DATETIME |  |    |

**範例：**
```json=
{
    "result": true,
    "errorCode": "",
    "message": "查詢成功",
    "data": {
        "userId": "10946012@ntub.edu.tw",
        "userName": "李O珊",
        "userSex": "女",
        "department": "",
        "role": "學生",
        "creatTime": "2023-04-19 03:40:20"
    }
}
```

---

#### 修改個人資訊
說明：

| General | 說明 | 
| --------------- | --- |
| Request Method  | PATCH |
| Request URL     | http://localhost:8080/user-account/profile |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |

**JSON：**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| userId | String | 使用者Google帳號 | 10946011@ntub.edu.tw | 必填 |
| userSex | int | 性別(男:0/女:1) | 1 | 非必填 |
| department | String | 所屬科系/班級 | 資管系 | 非必填 |

**範例：**
```json=
{
    "userId":"10946011@ntub.edu.tw",
    "userSex":"1",
    "department":"資管系"
}
```

**回傳：**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 | 
| ------ | ------- | --------- | ---- | --- |
| result | Boolean | API執行狀態 | true |    |
| errorCode | String | API執行異常代碼 | "" |    |
| message | String | API執行狀態說明 | "修改成功" |    |
| data | Optional<Object> |  |  |    |

**範例：**
```json=
{
    "result": true,
    "errorCode": "",
    "message": "修改成功",
    "data": {}
}
```

---

### 人員管理 
#### 全查
說明：查詢全部使用者帳號

| General | 說明 | 
| --------------- | --- |
| Request Method  | GET |
| Request URL     | http://localhost:8080/user-account?page= |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |

**Params**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| page     | INT     | 頁碼     | 1     | 後端會設定一頁查詢幾筆     |

**回傳**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| result     | Boolean | API執行狀態 | true |      |
| errorCode     | String | API執行異常代碼 | "" |      |
| message     | String | API執行狀態說明 | 查詢成功 |      |
| data    | List<Object> | 回傳資料 |      |      |
| userId  | String | 使用者Google帳號 |      |      |
| userName | String | 使用者名稱 |    |      |
| userSex | String | 性別(男/女) |    |  後端需判斷 0:男/1:女    |
| department | String     | 所屬科系/班級 |     |      |
| role | String | 角色/權限 |      |  對應codelist表role的desc    |
| available | Boolean | 啟用狀態(啟用:1/不啟用:0) |      |      |

**範例：**
```json=
{
    "result": true,
    "errorCode": "",
    "message": "查詢成功",
    "data": [
     {
            "userId": "10946038@ntub.edu.tw",
            "userName": "李冠賢",
            "userSex": "男",
            "department": null,
            "role": "學生",
            "available": true
        },
     {
            "userId": "10946012@ntub.edu.tw",
            "userName": "李姍珊",
            "userSex": "女",
            "department": "四技資管三甲",
            "role": "學生",
            "available": true
        },
 {
            "userId": "10946008@ntub.edu.tw",
            "userName": "楊玉珊",
            "userSex": "女",
            "department": "四技資管三甲",
            "role": "學生",
            "available": true
        }
    ]
}
```

---

#### 單查
說明：查詢單一使用者帳號

| General | 說明 | 
| --------------- | --- |
| Request Method  | GET |
| Request URL     | http://localhost:8080/user-account/{{Id}}  |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |
    
**Params**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| id     | String     | 使用者Google帳號     | 10946008@ntub.edu.tw |      |

**回傳**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| result     | Boolean | API執行狀態 | true |      |
| errorCode     | String | API執行異常代碼 | "" |      |
| message     | String | API執行狀態說明 | 查詢成功 |      |
| data    | Optional < Object > | 回傳資料 |      |      |
| userId  | String | 使用者Google帳號 |      |  |
| userName | String | 使用者名稱 |    |  |
| userSex | String | 性別(男/女) |    |  |
| department | String     | 所屬科系/班級 |     |  |
| role | String | 角色/權限 |      |      |
| available | Boolean | 啟用狀態(啟用:1/不啟用:0) |      |      |

**範例：**
```json=
{
    "result": true,
    "errorCode": "",
    "message": "查詢成功",
    "data": {
        "userId": "10946011@ntub.edu.tw",
        "userName": "周珮宣",
        "userSex": "女",
        "department": "四技資管三甲",
        "role": "學生",
        "available": true
    }
}
```

---

#### 總頁數查詢
說明：查詢人員管理總頁數

| General | 說明 | 
| --------------- | --- |
| Request Method  | GET |
| Request URL     | http://localhost:8080/user-account/count |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |

**回傳**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| result     | Boolean | API執行狀態 | true |      |
| errorCode     | String | API執行異常代碼 | "" |      |
| message     | String | API執行狀態說明 | 查詢成功 |      |
| data    | Optional < Object > | 回傳資料 |      |      |
| totalPage  | INT | 總頁數 |      |   |

**範例：**
```json=
{
    "result": true,
    "errorCode": "",
    "message": "查詢成功",
    "data": {
        "totalPage": 1
    }
}
```

---

#### 修改啟用狀態
說明：將使用者狀態改成啟用或不啟用

| General | 說明 | 
| --------------- | --- |
| Request Method  | PATCH |
| Request URL     | http://localhost:8080/user-account?id={{Id}} |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |

**Params**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| id     | String     | 使用者Google帳號     | 10946008@ntub.edu.tw |      |
    
**回傳**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| result     | Boolean | API執行狀態 | true |      |
| errorCode     | String | API執行異常代碼 | "" |      |
| message     | String | API執行狀態說明 | 查詢成功 |      |

**範例：**
```json=
{
    "result": true,
    "errorCode": "",
    "message": "修改成功",
    "data": {}
}
```

---

#### 模糊查詢
說明：根據使用者輸入的關鍵字查出相關帳號

| General | 說明 | 
| --------------- | --- |
| Request Method  | GET |
| Request URL     | http://localhost:8080/user-account/data?userId=&userName=&department=&page= |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |

Params

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| userId     | String     | 使用者Google帳號   |  |      |
| userName   | String     | 使用者名稱   | 李 |      |
| department  | String     | 所屬科系/班級   |  |      |
| page     | INT     | 頁碼   | 1 | 後端會設定一頁查詢幾筆 |
    
回傳

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| result     | Boolean | API執行狀態 | true |      |
| errorCode     | String | API執行異常代碼 | "" |      |
| message     | String | API執行狀態說明 | 查詢成功 |      |
| data     | List< Object> | 回傳資料 |  |      |
| userId     | String | 使用者Google帳號 |  |      |
| userName     | String | 使用者名稱 |  |      |
| userSex | String | 性別(男/女) |  | 後端需判斷 0:男/1:女 |
| department     | String | 所屬科系/班級 |  |      |
| role     | String | 角色/權限 |  | 對應codelist表role的desc |
| available | Boolean | 啟用狀態(啟用:1/不啟用:0) |  |  |
    
**範例：**

```json=
{
    "result": true,
    "errorCode": "",
    "message": "查詢成功",
    "data": [
     {
            "userId": "10946038@ntub.edu.tw",
            "userName": "李冠賢",
            "userSex": "男",
            "department": null,
            "role": "學生",
            "available": true
        },
     {
            "userId": "10946012@ntub.edu.tw",
            "userName": "李姍珊",
            "userSex": "女",
            "department": "四技資管三甲",
            "role": "學生",
            "available": true
        }
    ]
}
```

---

#### 模糊查詢的總頁數查詢
說明：根據使用者輸入的關鍵字查出相關帳號，後端設定一頁幾筆後回傳共幾頁

| General | 說明 | 
| --------------- | --- |
| Request Method  | GET |
| Request URL     | http://localhost:8080/user-account/data?userId=&userName=&department= |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |
    
回傳

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| result     | Boolean            | API執行狀態    | true    |      |
| errorCode  | String            | API執行異常代碼 | ""      |      |
| message    | String            | API執行狀態說明 | 查詢成功 |      |
| data       | Optional< Object> | 回傳資料        |         |      |
| totalPage  | INT               | 總頁數          |         |      |
    
**範例：**

```json=
{
    "result": true,
    "errorCode": "",
    "message": "查詢成功",
    "data": {
        "totalPage": 1
    }
}
```

---

## /summy-record
### 摘要紀錄 
#### 產生摘要
說明：將使用者傳入的content傳送到open ai api摘要存至summary_record表的summary欄位
同時也分類出諮商主題與情緒標籤，並分別存入資料庫

| General | 說明 | 
| --------------- | --- |
| Request Method  | POST |
| Request URL     | http://localhost:8080/summary-record |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |

**JSON：**
    
| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| content | TEXT | 諮商內容記錄 | 這次針對A學生的諮商... | 必填 |

**範例：**

```json=
{
    "content":"吵架好累，最近跟男友吵架，跟另一半吵架都怎麼和好呢？雖然只是小事，但有時候只是想男友哄哄我 嗚嗚嗚。"
}
```
    
**回傳：**

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 | 
| ------ | ------- | --------- | ---- | --- |
| result | Boolean | API執行狀態 | true |    |
| errorCode | String | API執行異常代碼 | "" |    |
| message | String | API執行狀態說明 | "查詢成功" |    |
| data | Optional<Object> | 回傳資料 |  |    |
    
**範例：**

```json=
{
    "result": true,
    "errorCode": "",
    "message": "摘要成功",
    "data": {}
}
```

---

#### 時間軸、摘要紀錄查詢
說明：用學號或姓名查出該學生的時間軸及內容摘要，其中學號是針對user_account表的user_id欄位做Like查詢

| General | 說明 | 
| --------------- | --- |
| Request Method  | GET |
| Request URL     | http://localhost:8080/summary-record?userId=&userName= |

| Headers | 說明 | 
| ------------- | ------------ |
| X-Auth-Token  | 登入者的token |

Params

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| userId     | String     | 學號   | 10946011  | 非必填     |
| userName   | String     | 姓名   | 周珮宣 |  非必填    |
    
回傳

| 參數名稱 | 參數型態 | 說明 | 範例 | 備註 |
| -------- | -------- | -------- | -------- | -------- |
| result     | Boolean | API執行狀態 | true |      |
| errorCode     | String | API執行異常代碼 | "" |      |
| message     | String | API執行狀態說明 | 查詢成功 |      |
| data     | List<Object> | 回傳資料 |  |      |
| userId     | String | 使用者Google帳號 | 10946011@ntub.edu.tw |      |
| userName     | String | 使用者名稱 | 周珮宣 |      |
| summaryRecord  | List<Object> | 回傳時間軸、內容摘要 |  |      |
| sId     | INT | 摘要紀錄表流水號 | 1 |      |
| establishTime | DATATIME | 對話建立時間(時間軸) | 2023-03-19 10:59:19 |      |
| summy     | TEXT | 內容摘要 | 最近我心情很糟... |      |
| consultationContent | TEXT | 諮商內容紀錄 | 針對A學生的... |   可能會是null   |
| modifyId     | String | 新增或修改的老師 | user_001 | 如果modifyId沒資料就抓createId     |

    
**範例：**

```json=
{
    "result": true,
    "errorCode": "",
    "message": "查詢成功",
    "data": [
        {
            "userId": "10946011@ntub.edu.tw",
            "userName": "周珮宣",
            "summaryRecord": [
                {
                    "sId": 1,
                    "establishTime": "2023-03-19 10:59:19",
                    "summy": "最近我跟男友吵架，雖然只是小事，但我想男友能哄哄我，不知道該如何和好。",
                    "consultationContent": "針對A學生的...",
                    "modifyId": "user_001"
                },
                {
                    "sId": 2,
                    "establishTime": "2023-04-30 10:59:19",
                    "summy": "最近我心情很糟，不知道怎麼緩解這個情緒。",
                    "consultationContent": null,
                    "modifyId": "user_001"


                }
            ]
        }
    ]
}
```
    
---
    
