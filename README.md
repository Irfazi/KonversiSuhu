# KonversiSuhu
 Tugas 2 - Irfazi - 2210010277
# 1. Deskripsi Program
Program Konversi Suhu ini adalah aplikasi sederhana berbasis Java yang memungkinkan pengguna untuk memasukkan nilai suhu dalam skala Celcius dan mengonversinya ke skala suhu lain, yaitu Fahrenheit, Reamur, atau Kelvin. Program ini dibuat menggunakan JFrame sebagai antarmuka pengguna dan dijalankan melalui NetBeans IDE 8.2.

* Pengguna memasukkan nilai suhu dan memilih jenis konversi

* Hasil konversi ditampilkan setelah tombol ditekan.

# 2. Komponen GUI ke JFrame
- JPanel: Sebagai panel utama untuk menampung komponen lainnya.
- JLabel: Untuk judul, label input suhu, dan label hasil konversi.
- JTextField: Untuk pengguna memasukkan nilai suhu.
- JComboBox: Untuk memilih skala suhu awal.
- JRadioButton: Untuk memilih skala suhu tujuan (misalnya Fahrenheit, Reamur, Kelvin).
- JButton: Untuk memproses konversi suhu.

Metode Konversi: 

* Tombol-tombol radio untuk memilih skala suhu awal.
Pilihan mode konversi suhu:
- Celsius ke skala lain
- Fahrenheit ke skala lain
- Kelvin ke skala lain
- Reamur ke skala lain
  
* Kotak kombo untuk memilih skala suhu tujuan.
Program ini memiliki metode konversi dari masing-masing skala suhu ke skala lainnya:
* celsiusToFahrenheit, celsiusToKelvin, celsiusToReamur
* fahrenheitToCelsius, fahrenheitToKelvin, fahrenheitToReamur
* kelvinToCelsius, kelvinToFahrenheit, kelvinToReamur
* reamurToCelsius, reamurToFahrenheit, reamurToKelvin

* Hasil konversi ditampilkan setelah tombol ditekan. Input suhu yang validasi otomatis untuk hanya menerima angka dan desimal.

# 3. Logika Program:
Rumus konversi, validasi input
   
# 4. Events

* ActionListener untuk tombol Konversi
~
private void btnKonversiActionPerformed(java.awt.event.ActionEvent evt) {                                            
       try {
        
            double inputSuhu = Double.parseDouble(suhuFiled.getText());
            String hasilKonversi = (String) cbxSkala.getSelectedItem();
            double hasil = 0.0;

        
        if (celcius.isSelected()) {
            
            switch (hasilKonversi) {
                case "Celsius ke Fahrenheit":
                    hasil = celsiusToFahrenheit(inputSuhu);
                    break;
                case "Celsius ke Kelvin":
                    hasil = celsiusToKelvin(inputSuhu);
                    break;
                case "Celsius ke Reamur":
                    hasil = celsiusToReamur(inputSuhu);
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Pilihan konversi tidak valid!");
                    break;
                    
            }
        } else if (fahrenheit.isSelected()) {
            
            switch (hasilKonversi) {
                case "Fahrenheit ke Celsius":
                    hasil = fahrenheitToCelsius(inputSuhu);
                    break;
                case "Fahrenheit ke Kelvin":
                    hasil = fahrenheitToKelvin(inputSuhu);
                    break;
                case "Fahrenheit ke Reamur":
                    hasil = fahrenheitToReamur(inputSuhu);
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Pilihan konversi tidak valid!");
                    break;    
            }
        } else if (kelvin.isSelected()) {
            switch (hasilKonversi) {
                case "Kelvin ke Celsius":
                    hasil = kelvinToCelsius(inputSuhu);
                    break;
                case "Kelvin ke Fahrenheit":
                    hasil = kelvinToFahrenheit(inputSuhu);
                    break;
                case "Kelvin ke Reamur":
                    hasil = kelvinToReamur(inputSuhu);
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Pilihan konversi tidak valid!");
                    break;
            }
        } else if (reamur.isSelected()) {
            switch (hasilKonversi) {
                case "Reamur ke Celsius":
                    hasil = reamurToCelsius(inputSuhu);
                    break;
                case "Reamur ke Fahrenheit":
                    hasil = reamurToFahrenheit(inputSuhu);
                    break;
                case "Reamur ke Kelvin":
                    hasil = reamurToKelvin(inputSuhu);
                    break;
                default:
                    JOptionPane.showMessageDialog(this, "Pilihan konversi tidak valid!");
                    break;
                }
            }

        hasilField.setText("" + hasil);
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Masukkan angka yang valid!");
        }
    
                        
    }
   ~   
* Tombol Konversi diklik akan menampilkan hasil konversi dari
~
// Dari Celsius ke skala lain
private double celsiusToFahrenheit(double celsius) {
    return (celsius * 9/5) + 32;
}

private double celsiusToReamur(double celsius) {
    return celsius * 4/5;
}

private double celsiusToKelvin(double celsius) {
    return celsius + 273.15;
}
// Dari Fahrenheit ke skala lain
private double fahrenheitToCelsius(double fahrenheit) {
    return (fahrenheit - 32) * 5/9;
}

private double fahrenheitToReamur(double fahrenheit) {
    return (fahrenheit - 32) * 4/9;
}

private double fahrenheitToKelvin(double fahrenheit) {
    return (fahrenheit - 32) * 5/9 + 273.15;
} 
~

5. Variasi:
* Tambahkan skala suhu lain seperti Reamur dan Kelvin
~
// Dari Kelvin
private double kelvinToCelsius(double kelvin) {
    return kelvin - 273.15;
}

private double kelvinToFahrenheit(double kelvin) {
    return (kelvin - 273.15) * 9/5 + 32;
}

private double kelvinToReamur(double kelvin) {
    return (kelvin - 273.15) * 4/5;
}
    
// Dari Reamur
private double reamurToCelsius(double reamur) {
    return reamur * 5/4;
}

private double reamurToFahrenheit(double reamur) {
    return reamur * 9/4 + 32;
}

private double reamurToKelvin(double reamur) {
    return reamur * 5/4 + 273.15;
}

~
* Tambahkan ItemListener pada JRadioButton untuk memilih arah konversi
~
  private void celciusItemStateChanged(java.awt.event.ItemEvent evt) {                                         
         if (evt.getStateChange() == ItemEvent.SELECTED) {
            cbxSkala.removeAllItems();
            cbxSkala.addItem("Celsius ke Fahrenheit");
            cbxSkala.addItem("Celsius ke Kelvin");
            cbxSkala.addItem("Celsius ke Reamur");
        }
    }                                        

    private void fahrenheitItemStateChanged(java.awt.event.ItemEvent evt) {                                            
        if (evt.getStateChange() == ItemEvent.SELECTED) {
            cbxSkala.removeAllItems();
            cbxSkala.addItem("Fahrenheit ke Celsius");
            cbxSkala.addItem("Fahrenheit ke Kelvin");
            cbxSkala.addItem("Fahrenheit ke Reamur");
        }
    }                                           

    private void reamurItemStateChanged(java.awt.event.ItemEvent evt) {                                        
        if (evt.getStateChange() == ItemEvent.SELECTED) {
            cbxSkala.removeAllItems();
            cbxSkala.addItem("Reamur ke Celsius");
            cbxSkala.addItem("Reamur ke Fahrenheit");
            cbxSkala.addItem("Reamur ke Reamur");
        }
    }                                       

    private void kelvinItemStateChanged(java.awt.event.ItemEvent evt) {                                        
        if (evt.getStateChange() == ItemEvent.SELECTED) {
            cbxSkala.removeAllItems();
            cbxSkala.addItem("Kelvin ke Celsius");
            cbxSkala.addItem("Kelvin ke Fahrenheit");
            cbxSkala.addItem("Kelvin ke Kelvin");
        }
    }

 ~
* Implementasikan konversi otomatis saat nilai input berubah
~
private void setupDocumentListener(){
       private void setupDocumentListener(){
        suhuFiled.getDocument().addDocumentListener(new DocumentListener() {
            @Override
            public void insertUpdate(DocumentEvent e) {
                btnKonversiActionPerformed();
            }

            @Override
            public void removeUpdate(DocumentEvent e) {
                btnKonversiActionPerformed();
            }

            @Override
            public void changedUpdate(DocumentEvent e) {
                btnKonversiActionPerformed();
            }        

            private void btnKonversiActionPerformed() {
                 
            }
        });  
    }
~

# Hasil Gambar Project Ketika di Run
![]().
## Indikator Penilaian:

| No  | Komponen         |  Persentase  |
| :-: | --------------   |   :-----:    |
|  1  | Komponen GUI     |    10    |
|  2  | Logika Program   |    20    |
|  3  | Kesesuaian UI    |    15    |
|  4  | Constructor      |    15    |
|  5  | Memenuhi Variasi |    40    |
|     | TOTAL        | 100 |

## Pembuat

Nama  : Irfazi
NPM   : 2210010277
