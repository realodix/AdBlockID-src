## 📃 Panduan Menulis Filter

Panduan ini dirancang untuk membantu Anda menulis dan mengelola filter.

- **Adblock Plus**: [How to write filters](https://help.adblockplus.org/adblock-plus-help-center/how-to-write-filters)
- **Adblock Plus**: [Adblock Plus filters explained](https://adblockplus.org/filter-cheatsheet)
- **AdGuard**: [How to create your own ad filters](https://adguard.com/kb/general/ad-filtering/create-own-filters/)
- **uBlock Origin**: [Static filter syntax](https://github.com/gorhill/uBlock/wiki/Static-filter-syntax)
- [Syntax meanings that are actually human readable](https://github.com/DandelionSprout/adfilt/blob/master/Wiki/SyntaxMeaningsThatAreActuallyHumanReadable.md)


## 📁 Struktur Direktori

Agar mudah di-maintain, daftar filter dipecah dan dikelompokkan ke dalam beberapa file.

```
/src
 ├─ /modules
 │   ├─ adult.adfl          [S] ...
 │   ├─ adult-block.adfl    [G] Blokir iklan berkonten dewasa.
 │   ├─ adult-hide.adfl     [G] Sembunyikan iklan berkonten dewasa.
 │   ├─ fandom.adfl         [All] Situs streaming, baca komik, dan lainnya.
 │   ├─ malaysia.adfl       [All] Situs berbahasa Melayu.
 │   └─ safelink.adfl       [All] Situs berjenis safelink/shortlink.
 ├─ /addons                 AdBlockID Addons
 │   ├─ /Annoyances             Filter annoyances
 │   │   └─ ...
 │   └─ ...
 ├─ anti-adblock.adfl       [G/S] Melumpuhkan ad block detection.
 ├─ extended.adfl           [S] Perbaiki tampilan situs setelah iklannya dihilangkan.
 ├─ general-block.adfl      [G] Blokir iklan.
 ├─ general-group.adfl      [G] ...
 ├─ general-hide.adfl       [G] Sembunyikan iklan.
 ├─ specific-block.adfl     [S] Blokir iklan.
 ├─ specific-hide.adfl      [S] Sembunyikan iklan.
 ├─ specific-hide_2.adfl    [S] ...
 └─ whitelist.adfl          [G/S] Mengembalikan sesuatu yang seharusnya ada, namun hilang
                            karena tidak sengaja terblokir/disembunyikan.
```

<sup>
* Penjelasan lengkap ada di masing-masing file. <br>
* [All]: Menangani berbagai hal seperti iklan, ad block detection, hingga annoyance. Filter bersifat spesifi dan general. <br>
* [G]: Filter bersifat general, tidak mengarah secara spesifik ke situs tertentu. <br>
* [S]: Filter bersifat spesifik, mengarah secara spesifik ke situs tertentu.
</sup>


## 🛠️ Pengelolaan

AdBlockID menggunakan [Haiku](https://github.com/realodix/haiku) sebagai *tools* untuk mengelola dan memelihara daftar filter.

### Instalasi

Jalankan command `composer install` di direktori root `AdBlockID-src`.

### Penggunaan

- `./vendor/bin/haiku lint`

  Memeriksa kesalahan dalam daftar filter.

  VSCode Task: `Lint`

- `./vendor/bin/haiku fix`

  Mengurutkan dan merapikan daftar filter.

  VSCode Task: `Fix`

- `./vendor/bin/haiku build`

  Menggabungkan semua filter (`/src`) menjadi satu file filter siap pakai (`/src`).

  VSCode Task: `Build`


## 🔗 Layanan Web

- [ABP Redundancy check](https://adblockplus.org/redundancy_check)
- [ABPVN Redundancy check](https://abpvn.com/ruleChecker/redundantRuleChecker.html)
