<div align="center">
    
The project still work and currently being rewritten for react and nest js. I think to finish within ~1.5 months. Stay in touch!

# Discord-Token-Checker
    
<img width="892" src="https://user-images.githubusercontent.com/49491499/170839591-6070cb63-1e1c-488d-8172-12a6978ab644.png">

## INSTALL    
</div>

```
pip install -r requirements.txt
```

```
python main.py
```
<div align="center">

## USAGE
</div>

1) Enter token. Accept: input text, any file (accept unparsed logs), folder (recursive scan files with tokens).
2) This program parses token with complex algorithms (check QUESTIONS for more info).
3) Then your tokens, check for validation using parallel request with highest speed. 
4) In the output you get text files with tokens and json_data file which contain all tokens data .
<div align="center">

## VIDEOS

[CLICK <br />![](https://user-images.githubusercontent.com/49491499/170839662-cf4f9872-3ece-4892-85b6-e18e84a28b0b.png)](https://youtu.be/dU0foZX8v5k)

[CLICK <br />![](https://user-images.githubusercontent.com/49491499/170839142-f1af441e-a63d-4ed5-abf2-023d687b0239.jpg)](https://youtu.be/mY648L5FqeA)

## QUESTIONS
</div>

1) Q: Could there be bugs in the code?

   A: Absolutely not. All methods used in the checker have been tested 1000 times by me, and the results have been verified with other checkers, including synchronous ones.

2) Q: Why is the sum of valid + unverified + invalid tokens less than the sum of parsed tokens?

   A: The checker records all id tokens. If the new token contains an id from the list of verified ones, it is removed. Don't worry if one token becomes invalid another token with the same id too.

3) Q: Why do I have 1000 tokens in the file, but the parser found only 580?

   A: The code uses an advanced token parser. The fact is that ordinary parsers check only the token pattern, but it also needs to check headers. (More info: https://jwt.io/introduction)
In short, there are tokens that were created by some kind of token generator. They contain a header. If you decrypt it (base64), then for natural discord tokens it represents json value, while for generated ones it will be different. Check it out for yourself: https://jwt.io/#debugger-io.
<div align="center">   

## OUTPUT
</div>
Standart output with valid, invalid, etc txt files.

Json output:
```json
{
    "tokensInfo": {
        "valid": [],
        "nitro": [],
        "payment": [],
        "phone": [],
        "unverified": [],
        "invalid": [],
        "parsedTokens": []
    },
    "tokensData": {
        "TOKEN": {
            "status": "valid || unverified || invalid",
            "me": {},
            "payment_sources": {}
        }
    }
}        
```
<div align="center">

</div>

## Changelog 2

After this amount of time, I'm ready to write a huge changelog for the project:
1) Added proxies to the checker, which increased the speed by n-times (depends on how many proxies are active on the server). I had to try to integrate them into the already complex request code.
2) Updated regexp for new tokens. Regarding this, a lot of settings have been moved to a backend to ensure stable operation of all versions. So, if anything, if the checker output is updated, you will also have it updated on the backend.
3) Unfortunately, I did not manage to make a site with a token checker. While there is not enough experience. BUT I'M TRYING TO FIX IT! Well, the fact that the site with the beta token checker began to block Google as a fraudulent site also began to dismoral me. After writing Google, everything worked, but not for long. :sad-trombone:
4) I had to discard such modules as nitroChecker, nitroPurchaser, info. They are hard to maintain code and I don't think they will be in demand.
5) An early update of the telegram bot is possible! Follow the news!
6) Fix api, now it looks not so clumsy.


## Changelog 1

Firstly, now the tokens data is processed on a remote server. This is due to the fact that I have been writing a telegram bot for checking tokens for a long time and I did not want to rewrite the backend for python.

In this regard, the speed increased from 1 token per second to 40. I achieved this with the help of parallel requests and proxies, it was difficult to implement in python. Also, when I finish the nuker, it will probably be the fastest, since the 429 error handler with limit checking will be used.

As soon as I complete the backend (checker, info, idTracker, webhookSpammer, nitroBuyer, serverNuker, userNuker, messageSearcher) I will publish it in the public.

Since 1 more request is needed for the final verification of tokens, then you get the payment sources as a side to discord.gg/users/@me.
Also due to the fact that you send tokens to the server, to avoid spam, there are one request per minute otherwise 429 error.

cpzgy