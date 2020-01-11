# 使用Heroku部署機器學習API

## [Medium 文章](https://medium.com/@andy6804tw/%E4%BD%BF%E7%94%A8heroku%E9%83%A8%E7%BD%B2%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92api-eca61ea711f1)

## 範例程式碼
這一個repo以手寫數字辨識為例，拿一個先已經訓練好的模型進行Python Flask API的開發與部署到Heroku。以下簡要說明Heroku雲端部署所需要的設定檔。

![](https://miro.medium.com/max/717/0*J8NOFIKZ78AqkMEK.png)

### Procfile 設定檔
Procfile 這個檔案是要告訴 Heroku 要如何啟動這個 web app，在 Heroku 裡，執行 Python 要使用 Gunicorn 來啟動 web server。所以在 requirements.txt 裡，請記得要輸入 gunicorn。Procfile 檔案，的內容如下。

```
web gunicorn run:app
```

### Aptfile 設定檔
由於我們的 AI 專案內需要使用 OpenCV 的套件，因此我們需要在Heroku中安裝 OpenCV 相關的套件。因為 Heroku 採 Linux 系統，因此我們要透過 apt 來安裝以下函式庫：
```
libsm6
libxrender1
libfontconfig1
libice6
```