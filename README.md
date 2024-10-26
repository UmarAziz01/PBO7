# PBO7
Penugasan matakuliah pemrograman berorientasi obyek pertemuan kesepuluh yakni membuat Report dengan Libary dan Plugin Java Eksternal dengan code dan database pada repositori sebelumnya yakni PBO_UTS

Link Download Library dan Plugin yang dibutuhan 

https://drive.google.com/drive/folders/12E6Avw_WMRfr2LmdsNi6VL3eu4o3m3DJ?usp=sharing

https://github.com/UmarAziz01/PBO_UTS

Berikut langkah-langkahnya

- Menduplikat Project yang telah dibuat dahulu saat UTS dan mengubah namanya dari PBO_UTS menjadi PBO_Report
  dengan cara klik kanan pada project PBO_UTS sehingga muncul gambar kurang lebih seperti ini
![image](https://github.com/user-attachments/assets/fe800976-d9ee-47a1-9884-2762db61a07f)
![image](https://github.com/user-attachments/assets/ef8f3c0b-ccc3-4add-b558-bd9ce2afa1bb)
Dan Klik “Copy” lalu setelah itu cari project dengan nama PBO_Report dan klik 2x

- Pastikan telah menambahkan Plugin iReport dan org-jdesktop-layout.
- Lalu tambahkan beberapa Library dengan file berekstensi jar
  dengan cara klik kanan pada library pada project yang dibuat tadi
  ![image](https://github.com/user-attachments/assets/4cd9b3cb-fad9-4c78-a0ac-77e1651f289d)
  ![image](https://github.com/user-attachments/assets/e3b12ce4-c9cb-4bad-be92-bf179539724f)
  ![image](https://github.com/user-attachments/assets/48b51f6c-f8e7-4300-aebf-e8cdb636e5cb)

- Tambahkan button baru ke frame yang dulu sudah dibuat dengan Nama Cetak dan Variable btnCetak
  ![image](https://github.com/user-attachments/assets/da83d727-9371-4476-b780-fb676a95c008)


- Lalu Klik dua kali pada button yang baru saja dibuat lalu salin kode ini dan tempelkan pada kode anda
  ````java
  private void btnCetakActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
        try {
            // TODO add your handling code here:
            Connection conn = DriverManager.getConnection("jdbc:postgresql://localhost:5432/PBO_UTS", "postgres", " ");
            String sql = "select * from mata_kuliah";
            Statement st = conn.createStatement();
            ResultSet rs = st.executeQuery(sql);
            File alamat = new File(".");
            System.out.println(alamat.getCanonicalPath());
            File jasperFile = new File(alamat.getCanonicalPath() + "/src/pbo_report/" + "Cetak.jrxml");
            JasperDesign jd = JRXmlLoader.load(jasperFile);
            JRResultSetDataSource jds = new JRResultSetDataSource(rs);
            JasperReport jr = JasperCompileManager.compileReport(jd);
            JasperPrint jp = (JasperPrint) JasperFillManager.fillReport(jr, new HashMap<String, Object>(), jds);
            JasperViewer.viewReport(jp);
        } catch (SQLException ex) {
            Logger.getLogger(CRUDForm.class.getName()).log(Level.SEVERE, null, ex);
        } catch (IOException ex) {
            Logger.getLogger(CRUDForm.class.getName()).log(Level.SEVERE, null, ex);
        } catch (JRException ex) {
            Logger.getLogger(CRUDForm.class.getName()).log(Level.SEVERE, null, ex);
        }
    }     
    

- Lalu buat satu Class baru dengan nama Cetak.jrxml
dengan cara klik kanan pada project dan klik new>other>Report>Report Wizard>Pilih Layout(Saya memilih Blank A4)> Klik Next > Beri Nama > Pilih/Buat koneksi ke database yang dahulu di UTS telah dibuat > Masukkan Query SQL yang diinginkan > Pilih Fields yang diinginkan > Next > Lakukan Grouping (Jika berkehendak) > Finish

![image](https://github.com/user-attachments/assets/477a5860-f58b-4ba5-9832-a01547d3307a)

- Lakukan Desain pada Class Cetak.jrxml tersebut
desain sesuai keinginan anda dan jangan lupa setelah selesai desain lakukan preview agar Class Cetak.jasper muncul secara otomatis pada project yang nantinya akan dipanggil pada GUI

![image](https://github.com/user-attachments/assets/cf3790eb-5efa-4305-a2a5-93d1b51e181a)
![image](https://github.com/user-attachments/assets/7983398a-d6b7-4c8e-b1e3-97046c0c5036)
![image](https://github.com/user-attachments/assets/2b1fd1a0-6c24-4f17-9d69-7494e5d5963a)

- Lakukan Clean and Build pada Project
  
![image](https://github.com/user-attachments/assets/ece5d4c6-3683-4b21-a2ec-da7414c2c890)

- Jika selesai jalankan program dan klik Button cetak tadi sehingga muncul seperti ini
  ![image](https://github.com/user-attachments/assets/84ab3577-c31e-4822-9e0a-47b485a20e53)
  
- Klik Cetak dan tunggu hasil report yang telah dibuat
  ![image](https://github.com/user-attachments/assets/1783432e-e7bb-4fb6-8775-d6ce72324d4d)

- Anda dapat melakukan penyimpanan dokumen dengan mengklik Tombol bergambar Printer dan lakukan penyimpanan dengan PDF pada direktori dan nama yang anda kehendaki

  Sekian Penjelasan singkat dari saya

