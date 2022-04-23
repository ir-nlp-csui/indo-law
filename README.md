# court-decisions

There are **22,630 court decision documents for general criminal cases** in the `dataset` folder. The files available are in **xml format**. The contents of the xml file are clean text generated from court decision documents in the form of pdf that available on the website of the [Indonesian Supreme Court Decision](https://putusan3.mahkamahagung.go.id/).

The main tag of each file is the `\<putusan\>` decision tag. The section of the decision is represented by eleven child tags. The eleven tags are `\<kepala_putusan\>\`, `\<identitas\>\`, `\<riwayat_penahanan\>\`, `\<riwayat_perkara\>\`, `\<riwayat_tuntutan\>\`, `\<riwayat_dakwaan\>\`, `\<fakta\>\`, `\<fakta_hukum\>\`, `\<pertimbangan_hukum\>\`, `\<amar_putusan\>\`, and `\<penutup\>\`. The following is a further explanation of the tags:

| No. | Document Sections | Strings That Often Identified the Sections |
| --- | --- | --- |
| 1. | Kepala putusan (*document opener*) | ‘PUTUSAN’ (‘*DECISION*’) Always in the first line |
| 2. | Identitas terdakwa (*defendant’s identity*) | ‘Nama...’, ‘Terdakwa I: Nama...’ (‘*Name ...*’, “*Defendant I: Name ...*”) |
| 3. | Riwayat perkara (*case history*) | ‘Para terdakwa didampingi oleh penasihat...’, ‘Pengadilan Negeri tersebut’ (‘*The defendants were accompanied by an adviser...*’) |
| 4. | Riwayat penahanan (*detention history*) | ‘Terdakwa ditahan dengan penahanan Rumah/Rutan/Kota/Negara oleh...’, ‘Terdakwa dalam perkara ini tidak ditahan’ (‘*The defendant was detained at Home/Detention Center/City/State detention by...*’, ‘*The defendant in this case was not detained*’) |
| 5. | Riwayat tuntutan (*prosecution history*) | ‘Telah/Setelah mendengar tuntutan...’ (‘*After hearing the demands...*’) |
| 6. | Riwayat dakwaan (*indictment history*) | ‘Menimbang, bahwa terdakwa... dakwaan Jaksa...’ (‘*Considering, that the defendant... the prosecutor’s indictment...*’) |
| 7. | Fakta (*facts*) | ‘Menimbang, bahwa dipersidangan telah mengajukan/mendengar/membaca/memeriksa...’ (‘*Considering, that at the court submitted/heard/read/examined...*’) |
| 8. | Fakta hukum (*legal facts*) | “Menimbang,... fakta-fakta/fakta hukum...” (“*Considering,... facts/legal facts...*”) |
| 9. | Pertimbangan hukum (*legal considerations*) | ‘Menimbang,... majelis hakim... berdasarkan fakta hukum/fakta-fakta...’ (‘*Considering,... the panel of judges... based on facts/legal facts...*’) |
| 10. | Amar putusan (*verdict*) | ‘MENGADILI’ (‘*JUDGE*’) |
| 11. | Penutup (*closing*) | ‘Demikianlah...’  (‘*Declares...*’) |


## Metadata court decision documents

In the main tag `\<putusan\>\` there are several parameters as metadata from the xml file. An example of a fragment from the verdict file is as follows:

```xml
<putusan amar="pidana" amar_lainnya="pidana-penjara-waktu-tentu" id="..." klasifikasi="pidana-umum" lama_hukuman="1650" lembaga_peradilan="pn-..." provinsi="jabar" status="berkekuatan-hukum-tetap" sub_klasifikasi="..." url="https://putusan3.mahkamahagung.go.id/direktori/putusan/....html">
  <kepala_putusan>
    putusan
    nomor ...
    demi keadilan berdasarkan ketuhanan yang maha esa
    pengadilan ... mengadili perkara pidana dengan acara pemeriksaan biasa dalam tingkat pertama menjatuhkan putusan sebagai berikut dalam perkara
  </kepala_putusan>
  <identitas>
    1 nama lengkap ...
    3 umur tanggal lahir ...
    4 jenis kelamin ...
    5 kebangsaan ...
    6 tempat tinggal ...
    7 agama ...
    8 pekerjaan ...
    9 pendidikan ...
  </identitas>
  <riwayat_penahanan>
    terhadap terdakwa telah dilakukan penangkapan berdasarkan surat perintah penangkapan ...
  </riwayat_penahanan>
  <riwayat_perkara>
    pengadilan negeri tersebut setelah membaca ...
  </riwayat_perkara>
  <riwayat_tuntutan>
    setelah mendengar pembacaan tuntutan pidana yang diajukan oleh penuntut umum yang pada pokoknya sebagai berikut ...
  </riwayat_tuntutan>
  <riwayat_dakwaan>
    menimbang bahwa terdakwa diajukan ke persidangan oleh penuntut umum didakwa berdasarkan surat dakwaan sebagai berikut ...
  </riwayat_dakwaan>
  <fakta>
    menimbang bahwa untuk membuktikan dakwaannya penuntut umum telah mengajukan saksi saksi sebagai berikut ...
  </fakta>
  <fakta_hukum>
    menimbang bahwa berdasarkan alat bukti yang diajukan berupa keterangan saksi surat dan keterangan terdakwa yang dihubungkan dengan barang bukti yang diajukan dalam perkara ini diperoleh fakta fakta hukum sebagai berikut ...
  </fakta_hukum>
  <pertimbangan_hukum>
    menimbang bahwa selanjutnya majelis hakim akan mempertimbangkan apakah berdasarkan fakta fakta hukum tersebut diatas terdakwa dapat dinyatakan ...
    mengingat pasal 351 ayat 3 jo pasal 55 ayat 1 ke 1 kuh pidana dan pasal 363 ayat 1 ke 4 kuh pidana undang undang ri no 8 tahun 1981 tentang kitab undang undang hukum acara pidana kuhap serta peraturan lain yang berkenaan dengan perkara ini
  </pertimbangan_hukum>
  <amar_putusan>
    mengadili
    1 menyatakan terdakwa ... telah terbukti secara sah dan meyakinkan bersalah melakukan tindak pidana penganiayaan yang mengakibatkan mati dan pencurian dalam keadaan memberatkan yang dilakukan secara bersama sama ...
  </amar_putusan>
  <penutup>
    demikianlah diputuskan dalam sidang permusyawaratan majelis hakim pengadilan negeri ...
  </penutup>
</putusan>
```
