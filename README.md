# EXPI Coin
Shell script to install or update [EXPI Masternode](https://expi.life) on a Linux server running Ubuntu 16.04.
***

## VPS installation
```
wget -q https://raw.githubusercontent.com/expicoin/expimn/master/expi.autoinstall.sh
bash expi.autoinstall.sh
```
***

## Desktop wallet setup

After the Masternode is up and running, you need to configure the desktop wallet accordingly. Here are the steps:
1. Open the EXPI Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **1000** EXPI to **MN1**.
4. Wait for 15 confirmations.
5. Go to **Help -> "Debug Window - Console"**
6. Type the following command: **masternode outputs**
7. Go to  **Tools -> "Open Masternode Configuration File"**
8. Add the following entry:
```
Alias Address Privkey TxHash TxIndex
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* TxIndex:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Select your MN and click **Start Alias** to start it.
13. Alternatively, open **Debug Console** and type:
```
startmasternode alias 0 MN1
```
14. Login to your VPS and check your masternode status by running the following command to confirm your MN is running:
```
expi-cli masternode status
```
***

## Usage:
```
expi-cli masternode status #To check your MN status
expi-cli getinfo #To get general info such as EXPI version and current block numnber
expi-cli mnsync status #To check if your MN is synced.
```
Also, if you want to check/start/stop **EXPI**, run one of the following commands as **root**:

```
systemctl status EXPI #To check if EXPI service is running
systemctl start EXPI #To start EXPI service
systemctl stop EXPI #To stop EXPI service
systemctl is-enabled EXPI #To check if EXPI service is enabled on boot
```
***
