![180663821-187214c4-7ac5-4b15-8c5a-0ca6a8d21dd9](https://user-images.githubusercontent.com/108091544/181376598-900610ab-9a4b-4c52-85b4-c8e30c661790.png)
# Near Stake Wars III için validator oluşturma işlemi adım adım anlatılmıştır. Yapılan görevler sonucunda 1 yıl kilitli olmak şartı ile 50000 adet Near token kazanma şansınız olacak.

# 1-)Cüzdan ve Cli Kurulumu

Öncelikle şu adrese gidiyoruz `https://wallet.shardnet.near.org` daha sonradan görsellerdeki gibi cüzdan oluşturuyoruz.

![1](https://user-images.githubusercontent.com/108091544/181381005-162db4f8-2684-471f-87c6-33b46a6c0b7d.PNG)
![2](https://user-images.githubusercontent.com/108091544/181381016-42e8c3c2-30a0-4275-8af2-fd7c2552e249.PNG)
![3](https://user-images.githubusercontent.com/108091544/181381018-a5fad5d0-c948-4ced-bb01-e65c7170efd6.PNG)

## Copy e basarak kelimeleri bir not defterine yapıştırıp kaydediyoruz. Bu bizim cüzdan adresimiz kelimeleri ve bunlar olmadan cüzdanımıza ulaşamayız. Kaybetmeyecek şekilde saklayın.
![4](https://user-images.githubusercontent.com/108091544/181381024-8fa6c516-f679-454f-96fe-cfb45848b757.PNG)
![5](https://user-images.githubusercontent.com/108091544/181381026-d60d0695-c860-47b3-876e-be8ac7cbc9e2.PNG)
![6](https://user-images.githubusercontent.com/108091544/181381028-51fa4ff0-8baa-48a4-b30f-c4317f9fbc5e.PNG)

## En son sağ üst tarafa tıklayarak ismimizin olduğu cüzdanı seçiyoruz ve cüzdan da test nearlarını görüyoruz. Cüzdan oluşturma işlemi bu kadardı.
![7](https://user-images.githubusercontent.com/108091544/181381031-93653bcd-4ff3-450c-91af-5163b41c2100.PNG)

## Şimdi Near-Cli yi Node'a yüklüyoruz. Sırasıyla kodları giriyoruz.
```
sudo apt update && sudo apt upgrade -y
```
```
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -  
sudo apt install build-essential nodejs
PATH="$PATH"
```
### Versiyon Kontrollerini yapıyoruz.
```
node -v
```
`v18.x.x`
```
npm -v
```
`8.x.x`

### En sonda yükleme Near-ClI kodunu gidiyoruz.
```
sudo npm install -g near-cli
```

### Yükleme işlemi sırasında şöyle bir ekran görünmeli
![8](https://user-images.githubusercontent.com/108091544/181581576-d4bbbe7b-0e8c-4d1a-804c-ed476b809479.PNG)

### Yükleme işlemi bittikten sonrada buna benzer kodların olduğu ekran gelmeli.
![9](https://user-images.githubusercontent.com/108091544/181581718-f6b564d6-90f7-41cd-ba3d-9412619fcd6a.PNG)

Doğru ağı seçmek için her yeni kabuk başlatıldığında ortamın ayarlanması gerekir.

Ağlar:

 -GuildNet
 -TestNet
 -Mainnet
 -Shardnet (Bu, Stake Wars için kullanacağımız ağdır)

### Sırasıyla kodları giriyoruz.
```
export NEAR_ENV=shardnet
echo 'export NEAR_ENV=shardnet' >> ~/.bashrc
```

### CLI denememizi sıradaki kodlarlar yapıyoruz. 

İlk kodla sıralamaya girmiş validatorleri ve durumlarını görebiliriz.
```
near proposals
```
İkinci kodla üretilen blok sayıları gibi ayrıntıları görebiliriz.
```
near validators current
```
Üçüncü kodla doğrulayıcılar arasına girecek olan nodeları görebiliriz.
```
near validators next
```

2-) Node Kurulumu

Kodu girdiğimizde ss'de ki gibi bir çıktı almalıyız.
![10](https://user-images.githubusercontent.com/108091544/181586114-46739e6a-5983-4441-9c16-f5f8cf45128b.PNG)

Güncelleme kodunu giriyoruz
```
sudo apt install -y git binutils-dev libcurl4-openssl-dev zlib1g-dev libdw-dev libiberty-dev cmake gcc g++ python docker.io protobuf-compiler libssl-dev pkg-config clang llvm cargo
```

Python pip yüklüyoruz
```
sudo apt install python3-pip
```
```
USER_BASE_BIN=$(python3 -m site --user-base)/bin
export PATH="$USER_BASE_BIN:$PATH"
```
```
sudo apt install clang build-essential make
```

Alttaki kodu girdikten sonra 
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
Eğer ss'de ki gibi bir ekranla karşılaşırsanız y yapıp enterlayın
![12](https://user-images.githubusercontent.com/108091544/181587914-249e8b67-d6b2-48e5-b359-21792598edb6.PNG)

Daha sonra bu ekranda bir şeye basmadan enterlayın sonra yükleme işlemi başlayacak bitiğinde 2. ssde ki gibi ekran görünmeli.
![13](https://user-images.githubusercontent.com/108091544/181588027-c080e898-dce4-416c-92d0-c74ac3d7d099.PNG)
![14](https://user-images.githubusercontent.com/108091544/181588041-3dd2e951-b993-425c-b854-d827138e29f4.PNG)

Sırasıyla kodları girmeye devam ediyoruz.

```
source $HOME/.cargo/env
```

### Dosyaları vps'e yükleme işlemine geçiyoruız. Kodları sırasıyla girmeye devam edelim.

```
git clone https://github.com/near/nearcore
cd nearcore
git fetch
git checkout 0d7f272afabc00f4a076b1c89a70ffc62466efe9
cargo build -p neard --release --features shardnet
```
Yukarıda girdiğimiz son kodla birlikte yükleme işlemi biraz vakit alıyor. Bittikten sonra alttaki kod ile dizini yüklüyoruz ve görüntü ss'de ki gibi olmalı.nearcore kılasörünün içinde olduğunuzdan emin olun.
```
./target/release/neard --home ~/.near init --chain-id shardnet --download-genesis
```
![15](https://user-images.githubusercontent.com/108091544/181659919-5d4e4873-01a1-4160-a82c-3c02ee68bbf4.PNG)

Kodlara devam ediyoruz.

```rm ~/.near/config.json
wget -O ~/.near/config.json https://s3-us-west-1.amazonaws.com/build.nearprotocol.com/nearcore-deploy/shardnet/config.json
```

Node çalıştırıyoruz.
```
cd ~/nearcore
./target/release/neard --home ~/.near run
```
Kırmızıyla işraretli olan yerin %100 olmasını bekliyorsunuz olduktan sonra Ctrl+c yapıp durduruyoruz logları.
![16](https://user-images.githubusercontent.com/108091544/181660598-3b30f8fe-df3e-40ba-bfd0-cf3ada3ae7e4.PNG)

## Node cüzdana bağlıyoruz. Bu ekrandan y yapıyoruz

```
near login
```
![17](https://user-images.githubusercontent.com/108091544/181661134-2e6f63ef-80f7-400b-9267-9fa119fa6115.PNG)

y yapınca alttaki ekranın gelmesi gerekiyor.

![19](https://user-images.githubusercontent.com/108091544/181661365-074b0787-9e0c-4a9a-87ec-9093928d2ffc.PNG)

Link kopyalayıp cüzdanın açtığımız yere yapıştırıyoruz.

