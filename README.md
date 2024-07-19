# Dill-validator Setup
![Screenshot](https://github.com/zhizhi1348/Dill-validator/blob/main/1_3SvzXxkw2SurI7QSX9y36w.png)

Follow Dill [Twitter](https://x.com/dill_xyz_)

Join [Discord](https://discord.com/invite/dill)

Validators [Explorer](https://andes.dill.xyz/validators)


**You must be choosen as Andes role in the discord to be able to join this Phase**

**Currently, People were selected in 2 phases and will be picked in 2 more phases in next 2 weeks**

**So Join Galxe [project](https://app.galxe.com/quest/Dill/GCVWntghfL) and be active in discord to get Andes role**

## Dependecies
```ruby
sudo apt update && apt upgrade -y
sudo apt install curl make wget clang net-tools pkg-config libssl-dev build-essential jq lz4 gcc unzip snapd -y
```

## Install Node
```ruby
cd $HOME && curl -O https://dill-release.s3.ap-southeast-1.amazonaws.com/linux/dill.tar.gz && \
tar -xzvf dill.tar.gz && cd dill

./dill_validators_gen new-mnemonic --num_validators=1 --chain=andes --folder=./
```
**Output:**
```
ubuntu@ip-xxxx:~/dill$ ./dill_validators_gen new-mnemonic --num_validators=1 --chain=andes --folder=./

***Using the tool on an offline and secure device is highly recommended to keep your mnemonic safe.***

Please choose your language ['1. العربية', '2. ελληνικά', '3. English', '4. Français', '5. Bahasa melayu', '6. Italiano', '7. 日本語', '8. 한국어', '9. Português do Brasil', '10. român', '11. Türkçe', '12. 简体中文']:  [English]: 3
Please choose the language of the mnemonic word list ['1. 简体中文', '2. 繁體中文', '3. čeština', '4. English', '5. Italiano', '6. 한국어', '7. Português', '8. Español']:  [english]: 4
Create a password that secures your validator keystore(s). You will need to re-enter this to decrypt them when you setup your Dill validators.:
Repeat your keystore password for confirmation:
The amount of DILL token to be deposited(2500 by default). [2500]:
This is your mnemonic (seed phrase). Write it down and store it safely. It is the ONLY way to retrieve your deposit.


Creating your keys.
Creating your keystores:	  [####################################]  1/1
Verifying your keystores:	  [####################################]  1/1
Verifying your deposits:	  [####################################]  1/1

Success!
Your keys can be found at: ./validator_keys


Press any key.
ubuntu@ip-xxxx:~/dill$
```

**Check if you created validator keys:**
```
ls -ltr ./validator_keys
```

**Import your keys to a keystore file:**
```
./dill-node accounts import --andes --wallet-dir ./keystore --keys-dir validator_keys/ --accept-terms-of-use
```

**Write the password you configured in the previous step into a file:**

``replace "your password" with your own``
```
echo "Your Password" > walletPw.txt
```

**Start light validator**
```
./start_light.sh -p walletPw.txt
```

Output: 
```
ubuntu@xxxxx:~/dill$ ./start_light.sh -p walletPw.txt
Option --pwdfile, argument 'walletPw.txt'
Remaining arguments:
using password file at walletPw.txt
start light node
start light node done
ubuntu@xxxxx:~/dill$ nohup: redirecting stderr to stdout
```
**Check health node**
```
./health_check.sh -v
```

## Faucet

``You must have Andes role in the discord to be able to join this phase``

``You can get faucet by typing $request `your-evm-address' in Andes channel``

## Delegate

**Transfer deposit-data file to local system**
> you can do it by using Filezilla or Termius via SFTP method
> Go to **/dill/validator_keys** directory and transfer **deposit_data-xxxx.json** file to your local system

### Upload and Delegate
1. Upload deposit_data-xxxx.json in https://staking.dill.xyz/
2. Connect to MetaMask (Site adds Dill Network automatically), Make sure you ahve >2500 $DILL tokens
3. Send Deposit & Sign you wallet transaction request

## Monitoring
1. Open your deposit_data-xxxx.json file and Copy your ``Pubkey``
2. Search it here: https://andes.dill.xyz/validators
3. Congrats you did it !

## Also Useful 

### Check Health
```
cd ~ && cd $HOME/dill
./health_check.sh -v
```
### Check Logs
```
cd ~ && cd $HOME/dill
tail -f -n 100 $HOME/dill/light_node/logs/dill.log
```

### Start Node
```
./start_light.sh -p walletPw.txt
```

***You can follow my [Twitter](https://x.com/zhiyarrr1) for futures tasks and updates***

