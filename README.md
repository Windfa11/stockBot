# stockBot
a bot use api of rasa and iexfinance to search stock info


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
