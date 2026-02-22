A.	Pendahuluan

Kanker kolorektal (Colorectal Cancer, CRC) menempati peringkat ketiga sebagai keganasan paling umum secara global dan penyebab kematian akibat kanker tertinggi kedua di dunia. Keterbatasan biomarker CRC menyebabkan sebagian besar kasus teridentifikasi pada stadium lanjut, sehingga diagnosis dini, penentuan prognosis, dan keberhasilan terapi menjadi terbatas. Oleh karena itu, penelitian ini bertujuan untuk mengidentifikasi gen inti (core genes, CGs) yang berperan dalam patogenesis CRC dan berpotensi sebagai biomarker untuk diagnosis dini, prognosis, serta pengembangan terapi.

B.	Metode

1.	Instalasi Perangkat Lunak

    a.	R 4.5.2
  
    Bahasa pemrograman R versi 4.5.2 diinstal melalui situs resmi Comprehensive R Archive Network (CRAN) (https://cran.r-project.org/) dengan memilih sistem operasi komputer yang sesuai, dalam hal ini menggunakan Windows, dengan meng-klik teks “Download R for Windows” dan memilih “install R for the first time” lalu “Download R-4.5.2 for Windows”. Proses instalasi perangkat lunak menggunakan pengaturan default. 

    b.	RStudio

    Perangkat lunak Rstudio versi 2026.01.1+403 diinstal melalui situs resmi Posit (https://posit.co/download/rstudio-desktop/) dengan meng-klik “Download RStudio Desktop for windows”. Proses instalasi perangkat lunak menggunakan pengaturan default.

2.	Analisis DEGs
  
	Analisis DEGs dilakukan menggunakan dataset Microarray GSE106582 dengan platform GPL10558 (Illumina HumanHT-12 V4.0) yang didapatkan melalui database GEO (https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE106582) yang berisi 194 sampel, yaitu 77 sampel jaringan tumor/CRC dan 117 sampel jaringan normal.

3.	GO Enrichment & KEGG Pathway

    Analisis GO Enrichment, meliputi biological processes (BPs), molecular function (MFs), dan Celllular Components (CCs) serta KEGG Pathway dilakukan melalui situs EnrichR (https://maayanlab.cloud/Enrichr/). Hasil analisis diurutkan berdasarkan nilai P value < 0.05.

C.	Hasil dan Interpretasi

1.	Identifikasi DEGs

  	Hasil analisis ekspresi gen pada dataset GSE106582 menunjukkan bahwa distribusi nilai ekspresi seluruh sampel, baik kelompok jaringan normal maupun jaringan tumor, normal dan seragam serta mengindikasikan bahwa tidak terdapat pergeseran distribusi ekspresi antar sampel. Lebar box pada masing-masing sampel seragam dan menunjukkan bahwa tingkat variasi ekspresi gen antar sampel relatif homogen dan tidak terdapat sampel dengan variabilitas yang menyimpang. Secara keseluruhan, visualisasi boxplot menunjukkan data yang stabil dan tidak menunjukkan adanya batch effect, sehingga dataset layak untuk dilanjutkan ke analisis diferensial ekspresi gen.

![Volcano Plot](Figures/plot.png)

  	Density plot menunjukkan bahwa distribusi nilai ekspresi gen pada kelompok jaringan normal dan jaringan tumor hampir sepenuhnya tumpang tindih. Bentuk kurva dengan adanya puncak pada log2 rendah menunjukkan adanya sebagian besar gen yang memiliki tingkat ekspresi sedang dan dengan adanya ekor panjang ke arah kanan menunjukkan adanya sejumlah kecil gen dengan ekspresi tinggi. Grafik tumpang tindih antar kedua kelompok menandakan tidak adanya pergeseran distribusi ekspresi gen antara jaringan normal dan tumor. Hal ini mengindikasikan bahwa perbedaan biologis kemungkinan terjadi pada subset gen tertentu dan bukan berupa perubahan seluruh transkriptom. Selain itu, kesamaan bentuk dan posisi kurva mengonfirmasi bahwa proses normalisasi dan transformasi telah menghasilkan distribusi yang konsisten antar kelompok dan menunjukkan tidak adanya batch effect.

  	UMAP plot menggambarkan pemisahan yang jelas antara kelompok jaringan normal dan jaringa tumor berdasarkan pola ekspresi gennya. Sampel tumor membentuk satu klaster di sisi kanan bawah, sedangkan sebagian besar sampel normal membentuk klaster terpisah di sisi kiri atas. Pemisahan ini mengindikasikan bahwa profil transkriptom antara jaringan normal dan tumor berbeda secara sistemik, bukan hanya pada sejumlah kecil gen. Adanya beberapa sampel yang berada di klaster yang tidak seharusnya mencerminakan kompleksitas dan heterogenitas dari jaringan tumor itu sendiri.

  	Volcano plot menunjukkan distribusi gen berdasarkan besar perubahan ekspresi logFC ≥ 0.5 (log2FC ≥ 1) untuk upregulated genes dan logFC ≤ -0.5 (log2FC ≤ -1) untuk downregulated genes serta tingkat signifikansi statistik −log10 adjusted p value 0.05. Dengan kriteria yang digunakan, teridentifikasi 1609 upregulated genes atau gen yang mengalami peningkatan ekspresi dan 1832 downregulated genes atau gen yang mengalami penurunan ekspresi. Hal ini mengindikasikan bahwa pada kondisi tumor terjadi kecenderungan penekanan ekspresi terhadap lebih banyak gen dibandingkan gen yang diinduksi ekspresinya.

  	Heatmap menampilkan pola ekspresi 50 gen teratas dengan perbedaan paling signifikan antara kelompok jaringan normal dan jaringan tumor berdasarkan nilai Z score per gen. Warna merah menunjukkan ekspresi tinggi, sedangkan biru menunjukkan ekspresi rendah dibandingkan rata rata gen tersebut di seluruh sampel. Adanya pemisahan klaster yang jelas antar kelompok sampel menunjukkan bahwa 50 gen tersebut memiliki kemampuan diskriminatif yang kuat untuk membedakan kedua kondisi.
 
3.	GO Enrichment & KEGG Pathway

  	Pada kategori Biological Processes, 50 gen tersebut berperan dalam Positive Regulation of Ubiquitin-Protein Transferase Activity, Xenobiotic Transport, Negative Regulation of Microtubule, dan proses biologis lainnya. Pada kategori Cellular Components, 50 gen terlibat dalam regulasi Basolateral Plasma Membrane, External Side of Apical Plasma Membrane, Lipid Droplet, dan komponen selular lainnya. Pada kategori Molecular Functions, 50 gen tersebut terlibat dalam Cyclase Activator Activity, Guanylate Cyclase Activator Activity, Ligand-Gated Monoatomic Anion Channel Activity, dan aktivitas fungsi molekuler lainnya. Sementara itu, berdasarkan analisis KEGG pathway, 50 gen tersebut hanya signifikan pada jalur Proximal Tubule Bicarbonate Reclamation. 

D.	Kesimpulan

Berdasarkan analisis ekspresi gen yang telah dilakukan, terdapat perbedaan transkriptomik yang jelas antara kelompok jaringan normal dan jaringan tumor. Hal ini ditunjukkan oleh pemisahan klaster yang jelas pada UMAP, distribusi gen signifikan pada volcano plot dengan 1609 gen upregulated dan 1832 gen downregulated yang mengikuti kriteria logFC ≥ 0.5 atau logFC ≤ -0.5 dan adjusted p value < 0.05, serta pola ekspresi yang kontras pada heatmap 50 gen paling signifikan yang mampu membedakan kedua kelompok secara konsisten. Temuan ini menunjukkan adanya disregulasi gen yang luas pada jaringan tumor yang kemungkinan berperan dalam proses proliferasi, perubahan diferensiasi sel, aktivasi jalur sinyal onkogenik, serta gangguan homeostasis jaringan, sehingga gen-gen yang teridentifikasi berpotensi menjadi kandidat biomarker diagnostik maupun target terapeutik, meskipun masih memerlukan validasi biologis dan analisis fungsional lanjutan untuk memastikan relevansi klinisnya.
