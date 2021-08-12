
<html >
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Token sale page">

    <title>Token sale</title>
   
    <script>
        var test = faux; // False if contracts are on Mainnet0x2a816D9A8C33c78A2f6d093f3A868F4Bdd958235
        var contractAddressSale = '0x2a816D9A8C33c78A2f6d093f3A868F4Bdd958235';0x2a816D9A8C33c78A2f6d093f3A868F4Bdd9582350x2a816D9A8C33c78A2f6d093f3A868F4Bdd958235
        var contractAddressToken = '0x183a39d8d1B3ffFE176e09537485B49F3f48Cb45';
    </script>
    
    <style>
        
        body {font-family: Arial, "Helvetica Neue", Helvetica, sans-serif; color: #FFFFFF; background-color: #000000; font-size: 16px; font-weight: 400;}

        h1 { font-size: 24px; font-weight: 700;} 
        h2 { font-size: 22px; font-weight: 500;}

        .small {
            font-size: 12px;
        }

        .err {
             color: #fa0707;
        }

        * {
          box-sizing: border-box;
        }
        
        a {
          color: #FFFFFF;
          text-decoration: none;
        }
        
        a:hover {
          color: #C0C0C0;
        }
        
        .clickable {
            cursor: pointer;
        }
        
        .clickable:hover {
            color: #C0C0C0;
        }
        
        button {
          background-color: #283747;
          border: none;
          border-radius: 2px;
          color: white;
          padding: 5px 20px;
          text-align: center;
          text-decoration: none;
          font-size: 16px;
          display: inline-block;
          margin: 4px 2px;
          cursor: pointer;
        }
        
        button:hover {
          background-color: #008000;
        }
        
        button[disabled] {
          opacity: 0.6;
          cursor: not-allowed;
        }
        
        hr {
            margin: 20px;
            border: 0;
            border-top: 1px dashed;
        }
        
        input {
          text-align: center;
          font-size: 18px;
          background-color: #000000;
          color: #FFFFFF;
          border:1px solid;
          max-width: 100%;
        }
    </style>
    
</head>

<body>
    
    <div style="text-align: center">
        <button id="connect" style="font-size: 12px">Connect</button>
        <span id="nometamask" class="err" style="display: none">Please install Metamask first...</span>
        <div class="network small"><span id="curnet"><span class="err">Please use DApp browser/extension (e.g. <a target="_blank" href="https://metamask.io">Metamask</a>)</span></span> <span id="myAddr"></span>
        <br>Referrer: <span id="referrer">none</span></div>
    </div>
    
    <div style="text-align: center">
        <h2>Token info</h2>
        <p><span id="tokenName">Yield Farming wallet</span> (<span id="tokenSymbol">YFW</span>)</p>
        <p><a target="_blank" href="0x183a39d8d1B3ffFE176e09537485B49F3f48Cb45" id="tokenAddress">0x183a39d8d1B3ffFE176e09537485B49F3f48Cb45</a></p>
        <!-- Reserved in case you want to show decimals and total supply: <span id="#tokenDecimalsUI"></span> <span id="#tokenSupplyUI"></span>-->
        <p><button id="addToken" style="text-align: center">Add to wallet</button></p>
    </div>
    
    <hr>
    
    <div style="text-align: center">
        <h2>Token sale info</h2>
        <p>Total sale quantity: <span id="quantity">800000000000</span></p>
        <p>Token price: <span id="price">0.0000000002</span> <span class='eth'>BNB</span> (<span id="ratio"></span> tokens per 1 BNB)</p>
        <p><progress id="progress" value="0" max="100" style="width: 70%"></progress></p>
        <p>Tokens sold: <span id="sold"></span></p>
        <p>Total raised: <span id="raised"></span> <span class='eth'>BNB</span></p>
        <p>Unsold tokens: <span id="unsold"></span></p>
        
        <p>Token sale status: <span id="status">--</span></p>
    </div>
    
    <hr>
    
    <div style="text-align: center">
        <h2>Buy tokens</h2>
        
        <p><input type="number" id="buyQty" value="1"></p>
        <h2><span id="buyAmount"></span> BNB</h2>
        <p><button id="buyBtn" style="text-align: center">Buy</button></p>
        <p>My tokens balance: <span id="myTokens"></span></p>
    </div>
    
    <hr>
    
    <div style="text-align: center">
        <h2>Sale contract</h2>
        <p>You can also buy tokens by sending BNB to this contract (gas limit min. 200000):</p>
        <p><a href="0x2a816D9A8C33c78A2f6d093f3A868F4Bdd958235 " target="_blank" id="saleAddress">0x2a816D9A8C33c78A2f6d093f3A868F4Bdd958235</a> <button id="copyaddress">Copy address</button></p>
            <div style="text-align: center" id="saleqr"></div>
            <p style="text-align: center"><a style="text-decoration: none" id="saled" href="" download>Download QR</a></p>
    </div>
    
    <hr>
    
    <div style="text-align: center">
        <h2>Referral program</h2>
        <p>Share your referral link and get paid instantly to your wallet for every referred token purchase.</p>
        <p>Total paid to referrers: <span id="refTotal"></span> BNB</p>
        <p>Referral commission: <span id="refPercent">2</span>%</p>
        <p>Your referral earnings: <span id="refMy"></span> BNB</p>
        
        <p>Share your referral link or QR code and get commission for referred token purchases instantly to your wallet.</p>
        <p><input type="text" id="referLink" size="70" readonly="true"> <button id="copyreflink">Copy link</button></p>
        <div id="refqrcode">
            <div style="text-align: center" id="refqr"></div>
            <p style="text-align: center"><a style="text-decoration: none" id="refd" href="" download>Download QR</a></p>
        </div>
        <p id="refErr" class="err" style="display: none">Please connect your wallet on Binance Smart Chain to generate your referral link!</p>
    </div>
    
<script src='https://dappbuilder.org/js/jquery-3.6.0.min.js' type="text/javascript" charset="utf-8"></script> 
<script src='https ://dappbuilder.org/js/ethers-5.0.umd.min.js' type="text/javascript" charset="utf-8"></script> 
<script src='https://dappbuilder.org /bsc/tokensalewithreferral/js/tokensale.ui.js' type="text/javascript" charset="utf-8"></script> 

</body> 
</html>
            

            
