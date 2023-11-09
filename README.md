
# Hoyo-Daily Check-in

A lightweight, secure, and free script that automatically collect HoYoLAB daily check in rewards.
Supports Genshin Impact, Honkai Impact 3rd, and Honkai: Star Rail. Support multiple accounts.


## Features


   - Lightweight - The script only requires minimal configuration and is only 90 lines of code.
   - Secure - The script can be self-deployed to Google Apps Script, no worries about data leaks.
   - Free - Google Apps Script is currently a free service.
   - Simple - The script can run without a browser and will automatically notify you through Discord or Telegram.



## Setup


   1. Go to Google Apps Script and create a new project with your custom name.

   2. Select the editor and paste the code. Refer to the instructions below to configure the config file and save it.

  3. Select "main" and click the "Run" button at the top.Grant the necessary permissions and confirm that the configuration is correct (Execution started > completed).

 4. Click the trigger button on the left side and add a new trigger.

     Select the function to run: main.

     Select the event source: Time-drive

     Select the type of time based trigger: Day timer
          
     Select the time of day: recommended to choose any off-peak time between 0900 to 1500.

## getToken
```
function getCookies(name) {
  const value = `${document.cookie}`;
  const parts = value.split(`; `);

  const sortParts = parts.filter((part) => {
    return (
      part.includes('account_mid_v2') ||
      part.includes('account_id_v2') ||
      part.includes('ltoken_v2') ||
      part.includes('ltmid_v2') ||
      part.includes('ltuid_v2')
    );
  });
  const profile = {
    token: `ltoken_v2= ;` + sortParts.join(';'),
    genshin: true,
    honkai_star_rail: true,
    honkai_3: false,
    accountName: name,
  };
  return JSON.stringify(profile, null);
}
```
1. Paste the code into your console after you logged in with your hoyo-account and press enter, call the function and then input your name as an argument
![App Screenshot](https://cdn.discordapp.com/attachments/1022520064924209223/1172158788564955176/QS10Z5W.png?ex=655f4cf0&is=654cd7f0&hm=8ce2984e4299348f2a1005019feaa04b98be83de3514e33f902f01c23ed0fd3a&)


2. get the ltoken_v2 from the Application Tab>Cookies as it is protected and cannot be retrieved by document.cookie method

3. paste the ltoken_v2 to the returned value of getCookies()

## Setup Script

1. Go to Project Settings

2. set property to "profiles" and for the value put it inside an array and paste the token config that you got earlier.

![App Screenshot](https://cdn.discordapp.com/attachments/1022520064924209223/1172160088694337546/YSLwTLJ.png?ex=655f4e26&is=654cd926&hm=ab1214cf7c57cfed9d493335b88cf513efb90c88c623b34f913c50070874eb27&)

3. Profit!!!
