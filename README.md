# StockBot

## Demo
### stock price enquiry
![image](https://github.com/Windfa11/stockBot/blob/master/demo/stock_price.gif)

### market capitalization enquiry
![image](https://github.com/Windfa11/stockBot/blob/master/demo/marketCap.gif)

### trading volume enquriy
![image](https://github.com/Windfa11/stockBot/blob/master/demo/trading_volume.gif)

## Introduction
* a bot use api of rasa-nlu and iexfinance to search stock info
* the paser is spacy
* pipline of rasa is sklearn

## Init

### install rasa
        git clone https://github.com/RasaHQ/rasa_nlu.git
        cd rasa_nlu
        pip install -r requirements.txt
        pip install -e .

### install spacy
        pip install spacy
        python -m spacy download en_core_web_sm
        python -m spacy download en

### install iexchange
        pip3 install iexfinance


### Running Bot
* Open **telegram.ipynb** in jupyter notebook or pygram.
* Or you could paste to a file and run as a normal python  script

you should change the bot token in **telegram.ipynb**, and you can apply it at [here](https://iexcloud.io)

#### possible issue
Result of the telegram  internal proxy issue, this bot is dricetly base on HTTP request insteasd of API methods to receive user input. It use the *getUpdates*  interface which will receive all recent messages repeatedly (even if the bot have recieved these message). Therefore, when the interface accumulate a large number of data and sending to the script, it will lead the stack overflow. 

##### solution
1. Waiting for the server to clean the cache
2. Run the API methods (if your internet without proxy issue) to recieve the message once and it will clean the message stack
``` python
    import time
    import telepot
    from telepot.loop import MessageLoop

    def handle(msg):
        content_type, chat_type, chat_id = telepot.glance(msg)

        if content_type == 'text':
            replyMessage(chat_id, msg):

    bot = telepot.Bot(bot_token)
    MessageLoop(bot, handle).run_as_thread()
    print ('Listening ...')

    while 1:
        time.sleep(10)
 ```
