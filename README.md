# indo-law: Indonesian law dataset containing section annotation of court decision documents


## Introduction
This dataset consists of **Indonesian court decision documents** for general criminal cases that have been annotated for the document sections. There are **22,630 documents** in the `dataset` folder. The documents are available in **xml format**. The contents of the xml file are clean text extracted from the PDF files of court decision documents that are publicly available on the website of the [Indonesian Supreme Court Decision](<a href="https://putusan3.mahkamahagung.go.id/">https://putusan3.mahkamahagung.go.id/</a>)

11 sections were annotated from each court decision document: `<kepala_putusan>` (*document opener*), `<identitas>` (*defendant’s identity*), `<riwayat_penahanan>` (*case history*), `<riwayat_perkara>` (*detention history*), `<riwayat_tuntutan>` (*prosecution history*), `<riwayat_dakwaan>` (*indictment history*), `<fakta>` (*facts*), `<fakta_hukum>` (*legal facts*), `<pertimbangan_hukum>` (*legal considerations*), `<amar_putusan>` (*verdict*), and `<penutup>` (*closing*). These sections were used in our work to predict the category and the length of punishment in Indonesian courts using a deep learning model CNN+attention (Please see the end of this README file to see the reference to our paper that explains about this work). 

The following is a detail explanation of each annotated section:

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


## Dataset description

Each document in this dataset is in the XML format. Each file contains one main tag `<putusan>` that encloses several tags, which corresponds to the document sections.  An example of a text fragment of XML file is as follows:

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


## Note

The distribution of **training and testing data** used in our work was **90:10 portions** for each category (see Table 1 on <a href="https://www.mdpi.com/2073-431X/11/6/88">our paper</a>). Unfortunately we cannot provide that data split used in our experiment because it was not backed up.


## References
Please cite the following paper if you use this dataset:

**Nuranti, E. Q., Yulianti, E., & Husin, H. S.** (2022). <a href="https://www.mdpi.com/2073-431X/11/6/88">Predicting the Category and the Length of Punishment in Indonesian Courts Based on Previous Court Decision Documents.</a> Computers, 11(6), 88.


## License
You can use this dataset for free. You don't need our permission to use it. Please cite our paper if your work uses our data in your publication. Please note that you are not allowed to create a copy of this dataset and share it publicly in your own repository without our permission.

## Contact
**evi.y [at] cs.ui.ac.id**
