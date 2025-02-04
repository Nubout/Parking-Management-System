import matplotlib.pyplot as plt
import numpy as np  # Import numpy

class ParkiranMall:
    def __init__(self, kapasitas):
        self.kapasitas = kapasitas
        self.parkiran = [None] * kapasitas
        self.terisi = 0

    def parkir_mobil(self, plat_nomor):
        if self.terisi < self.kapasitas:
            for i in range(self.kapasitas):
                if self.parkiran[i] is None:
                    self.parkiran[i] = plat_nomor
                    self.terisi += 1
                    print(f"Mobil dengan plat nomor {plat_nomor} berhasil diparkir di slot {i + 1}.")
                    return
        else:
            print("Parkiran penuh!")

    def keluar_mobil(self, plat_nomor):
        for i in range(self.kapasitas):
            if self.parkiran[i] == plat_nomor:
                self.parkiran[i] = None
                self.terisi -= 1
                print(f"Mobil dengan plat nomor {plat_nomor} berhasil keluar dari slot {i + 1}.")
                return
        print(f"Tidak ditemukan mobil dengan plat nomor {plat_nomor} di parkiran.")

    def tampilkan_parkiran(self):
        print("Status Parkiran:")
        for i in range(self.kapasitas):
            status = self.parkiran[i] if self.parkiran[i] is not None else "Kosong"
            print(f"Slot {i + 1}: {status}")

    def tampilkan_parkiran_visual(self):
        # Membuat grafik batang untuk status parkiran
        status = ['Terisi' if slot is not None else 'Kosong' for slot in self.parkiran]
        
        # Menyiapkan data untuk visualisasi
        terisi_count = status.count('Terisi')
        kosong_count = status.count('Kosong')

        # Membuat plot
        labels = ['Terisi', 'Kosong']
        values = [terisi_count, kosong_count]

        plt.bar(labels, values, color=['green', 'red'])
        plt.title('Status Parkiran Mall')
        plt.xlabel('Status')
        plt.ylabel('Jumlah Slot')
        plt.show()

    def simpan_status(self, nama_file):
        with open(nama_file, 'w') as file:
            for plat_nomor in self.parkiran:
                file.write(f"{plat_nomor}\n")
        print("Status parkiran berhasil disimpan ke file.")

    def muat_status(self, nama_file):
        try:
            with open(nama_file, 'r') as file:
                self.parkiran = [line.strip() if line.strip() != 'None' else None for line in file]
                self.terisi = sum(1 for plat in self.parkiran if plat is not None)
            print("Status parkiran berhasil dimuat dari file.")
        except FileNotFoundError:
            print("File tidak ditemukan.")

def main():
    try:
        kapasitas = int(input("Masukkan kapasitas parkiran: "))
        if kapasitas <= 0:
            raise ValueError("Kapasitas harus lebih besar dari 0.")
    except ValueError as e:
        print(f"Input salah: {e}")
        return

    parkiran_mall = ParkiranMall(kapasitas)
    
    while True:
        print("\nMenu:")
        print("1. Parkir Mobil")
        print("2. Keluar Mobil")
        print("3. Tampilkan Status Parkiran")
        print("4. Tampilkan Visualisasi Status Parkiran")
        print("5. Simpan Status Parkiran ke File")
        print("6. Muat Status Parkiran dari File")
        print("7. Keluar")
        
        try:
            pilihan = int(input("Pilih opsi (1-7): "))
            if pilihan == 1:
                plat_nomor = input("Masukkan plat nomor mobil: ")
                parkiran_mall.parkir_mobil(plat_nomor)
            elif pilihan == 2:
                plat_nomor = input("Masukkan plat nomor mobil: ")
                parkiran_mall.keluar_mobil(plat_nomor)
            elif pilihan == 3:
                parkiran_mall.tampilkan_parkiran()
            elif pilihan == 4:
                parkiran_mall.tampilkan_parkiran_visual()  # Menampilkan visualisasi
            elif pilihan == 5:
                nama_file = input("Masukkan nama file untuk menyimpan status parkiran: ")
                parkiran_mall.simpan_status(nama_file)
            elif pilihan == 6:
                nama_file = input("Masukkan nama file untuk memuat status parkiran: ")
                parkiran_mall.muat_status(nama_file)
            elif pilihan == 7:
                print("Terima kasih! Sampai jumpa.")
                break
            else:
                print("Opsi tidak valid. Coba lagi.")
        except ValueError:
            print("Input salah. Harap masukkan angka 1-7.")

if __name__ == "__main__":
    main()
