# MIRA OS Kernel

MIRA OS'un Linux çekirdeği yapılandırma deposu. Bu çalışma, Linux stable **v6.18.60** kaynak ağacını temel alır; bu depoda Linux çekirdeğinin tamamı bulunmaz.

## Mevcut durum

- Hedef mimari: `x86_64`
- Deneme bilgisayarı: Dell Inspiron 5558, Intel Core i7-5500U (Broadwell)
- Yapılandırma sürüm eki: `-mira-os` (`6.18.60-mira-os`)
- Bu anlık görüntü yalnızca yapılandırma ve proje belgelerini içerir; henüz MIRA'ya özgü çekirdek kaynak kodu değişikliği yoktur.
- Önceki derleme denemesi, bulunmayan `debian/canonical-certs.pem` dosyasını aradığı için durmuştu. Yayımlanan yapılandırmada `CONFIG_SYSTEM_TRUSTED_KEYS` ve `CONFIG_SYSTEM_REVOCATION_KEYS` boş bırakılarak bu dosya referansları kaldırıldı.
- Bu düzeltmeyle yapılmış başarılı bir tam derleme henüz doğrulanmadı; bu depoda önyüklenebilir çekirdek veya kurulum paketi yoktur.

## Yapılandırma

[`configs/mira-os-6.18.60-x86_64.config`](configs/mira-os-6.18.60-x86_64.config), yerel Linux 6.18.60 ağacındaki güncel `.config` dosyasının kopyasıdır. Önceki `mira_broadwell_defconfig` yedeğinden farklı olarak MIRA sürüm ekini ve sertifika yolları düzeltmesini içerir.

## Kaynak sürümü

- Upstream: [Linux stable](https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git)
- Etiket: `v6.18.60`
- Kaynak commit: `f45ed76d6791cf72ff1265ee93511175bbbc2f18`

## Yeniden oluşturma

Önce upstream kaynak kodunu alın, yapılandırmayı yükleyin ve sürüm adını doğrulayın:

```bash
git clone --depth 1 --branch v6.18.60 https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git linux-6.18
cd linux-6.18
cp /path/to/MIRA-OS-Kernel/configs/mira-os-6.18.60-x86_64.config .config
make olddefconfig
make -s kernelrelease
```

Son komutun `6.18.60-mira-os` yazması beklenir. Tam derleme ve açılış doğrulaması bu anlık görüntüde tamamlanmış değildir.

## Lisans

Linux çekirdeği GPL-2.0 lisanslıdır. Lisans metni [LICENSE](LICENSE) dosyasındadır.
