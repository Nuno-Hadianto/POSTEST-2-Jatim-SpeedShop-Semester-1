Jatim SpeedShop Program

```

from prettytable import PrettyTable

# Inisialisasi daftar part
daftar_part = []
part_id = 1

# Fungsi untuk menambahkan part ke daftar
def tambah_part():
    global part_id
    nama_part = input("Masukkan nama part: ")
    harga_part = float(input("Masukkan harga part: "))
    stock_part = int(input("Masukkan stok part: "))
    part = {
        "ID": part_id,
        "Nama Part": nama_part,
        "Harga": harga_part,
        "Stok": stock_part,
    }
    daftar_part.append(part)
    part_id += 1
    print("Part berhasil ditambahkan.")

# Fungsi untuk menampilkan daftar part
def tampilkan_part():
    table = PrettyTable()
    table.field_names = ["ID", "Nama Part", "Harga", "Stok"]
    for part in daftar_part:
        table.add_row([part["ID"], part["Nama Part"], part["Harga"], part["Stok"]])
    print(table)

# Fungsi untuk mengupdate part berdasarkan ID
def update_part():
    tampilkan_part()
    id_part = int(input("Masukkan ID part yang akan diupdate: "))
    for part in daftar_part:
        if part["ID"] == id_part:
            nama_part = input("Masukkan nama part baru: ")
            harga_part = float(input("Masukkan harga part baru: "))
            stock_part = int(input("Masukkan stok part baru: "))
            part["Nama Part"] = nama_part
            part["Harga"] = harga_part
            part["Stok"] = stock_part
            print("Part berhasil diupdate.")
            return
    print("Part dengan ID tersebut tidak ditemukan.")

# Fungsi untuk menghapus part berdasarkan ID
def hapus_part():
    tampilkan_part()
    id_part = int(input("Masukkan ID part yang akan dihapus: "))
    for part in daftar_part:
        if part["ID"] == id_part:
            daftar_part.remove(part)
            print("Part berhasil di delete.")
            return
    print("Part dengan ID tersebut tidak ditemukan.")

# Fungsi untuk melakukan transaksi
def transaksi():
    tampilkan_part()
    id_part = int(input("Masukkan ID part yang akan dibeli masseh: "))
    for part in daftar_part:
        if part["ID"] == id_part:
            if part["Stok"] > 0:
                jumlah = int(input("Masukkan jumlah yang akan dibeli masseh: "))
                if jumlah <= part["Stok"]:
                    total = jumlah * part["Harga"]
                    print(f"Total harga: {total}")
                    part["Stok"] -= jumlah
                    print("Transaksi berhasil!!!")
                    return
                else:
                    print("Stok tidak mencukupiii.")
                    return
    print("Part Racing ID tersebut tidak ada atau habis masseh.")

# Fungsi utama
def main():
    while True:
        print("\nPilih Role Anda:")
        print("1. Administrator")
        print("2. Buyer")
        print("3. Exit Masseh")
        
        role = input("Pilih Role (1/2/3): ")
        
        if role == '1':
            username = input("Masukkan Username :")
            password = input("Masukkan Password :")
            print("\n===== SuperUser =====")
            print(username)
            print(password)

            while True:
                print("\n===== Jatim SpeedShop =====")
                print("1. Tampilkan List Part Racing (Administrator)")
                print("2. Tambah Part Racing (Administrator)")
                print("3. Update Part Racing (Administrator)")
                print("4. Delete Part Racing (Administrator)")
                print("5. Back")
                
                administrator_choice = input("Pilih tindakan administrator (1/2/3/4/5): ")
                
                if administrator_choice == '1':
                    tampilkan_part()
                elif administrator_choice == '2':
                    tambah_part()
                elif administrator_choice == '3':
                    update_part()
                elif administrator_choice == '4':
                    hapus_part()
                elif administrator_choice == '5':
                    break
                else:
                    print("Pilihan tidak valid.")
        elif role == '2':
            print("\nMenu Buyer:")
            print("1. Transaksi")
            print("2. Back")
            
            buyer_choice = input("Pilih tindakan buyer (1/2): ")
            
            if buyer_choice == '1':
                transaksi()
            elif buyer_choice == '2':
                tampilkan_part()
                print("dibeli lah xixixi, lihat dulu tabel diatas, sangat menggiurkan ya kan???")
            else:
                print("Pilihan tidak benar.")
        elif role == '3':
            print("Exit From Jatim SpeedShop Applcation.")
            break
        else:
            print("Pilihan tidak benar.")            
    
if  "__main__":
    main()

```
