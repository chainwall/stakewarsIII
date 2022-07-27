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
Versiyon Kontrollerini yapıyoruz.
```
node -v
```
`v18.x.x`
```
npm -v
```
`8.x.x`

En sonda yükleme kodunu gidiyoruz.
```
sudo npm install -g near-cli
```


