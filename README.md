Jatim SpeedShop Application

```

from prettytable import PrettyTable

# Inisialisasi daftar part recink
daftar_part = []
part_id = 1

# Fungsi untuk menambahkan part recink ke daftar
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

# Fungsi untuk menampilkan daftar part recink
def tampilkan_part():
    table = PrettyTable()
    table.field_names = ["ID", "Nama Part", "Harga", "Stok"]
    for part in daftar_part:
        table.add_row([part["ID"], part["Nama Part"], part["Harga"], part["Stok"]])
    print(table)

# Fungsi untuk mengupdate part recink berdasarkan ID
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

# Fungsi untuk menghapus part recink berdasarkan ID
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

** Penjelasan Program **

Program di atas adalah sebuah aplikasi untuk mengelola daftar "Part Racing" yang dapat dibeli dan melakukan transaksi. Aplikasi ini memiliki dua role, yaitu Administrator dan Buyer. lalu Import Library: Program mengimpor modul PrettyTable untuk membuat tabel yang rapih saat menampilkan daftar part. kemudian Inisialisasi Daftar Part: Program membuat sebuah daftar kosong bernama "daftar_part" yang akan digunakan untuk menyimpan informasi tentang part racing. Kemudian, program menginisialisasi variabel "part_id" dengan nilai 1, yang akan digunakan untuk memberikan ID kepada setiap part yang ditambahkan berupa angka. setelah itu Fungsi tambah_part(): Fungsi ini memungkinkan Administrator untuk menambahkan part racing baru ke dalam daftar. user diminta untuk memasukkan nama part, harga, dan stok part. Data part tersebut kemudian disimpan dalam bentuk dictionary(semacam itu) dan ditambahkan ke daftar "daftar_part" bersama dengan ID yang unik. ID part diberikan secara otomatis.lalu Fungsi tampilkan_part(): Fungsi ini digunakan untuk menampilkan daftar part racing dalam bentuk tabel dengan menggunakan modul PrettyTable. Informasi yang ditampilkan meliputi ID, Nama Part, Harga, dan Stok dari setiap part. setelah itu Fungsi update_part(): Fungsi ini memungkinkan Administrator untuk mengupdate informasi sebuah part racing berdasarkan ID. user diminta untuk memasukkan ID part yang akan diupdate, dan jika ID tersebut ditemukan dalam daftar, pengguna dapat memasukkan informasi baru seperti nama part, harga, dan stok. kemudian Fungsi hapus_part(): Fungsi ini memungkinkan Administrator untuk menghapus part racing berdasarkan ID yang dimasukkan/inputkan. user diminta untuk memasukkan ID part yang akan dihapus, dan jika ID tersebut ditemukan dalam daftar, part tersebut akan dihapus dari daftar. habistu Fungsi transaksi(): Fungsi ini digunakan oleh Buyer untuk melakukan transaksi pembelian part racing. user diminta untuk memasukkan ID part yang akan dibeli, dan jika part tersebut tersedia (stok lebih dari 0) dan jumlah yang diminta tidak melebihi stok yang ada, transaksi akan berhasil. Harga total ditampilkan dan stok part akan dikurangi sesuai dengan jumlah yang dibeli buyer. nahh lalu Fungsi main(): Fungsi utama program yang berisi loop utama. user diminta untuk memilih peran (Administrator, Buyer, atau Keluar/Back ). Terdapat loop tambahan untuk Administrator yang dapat menjalankan tindakan seperti menampilkan, menambahkan, mengupdate, atau menghapus part racing. Loop Buyer memungkinkan pembelian part racing atau melihat daftar part. Loop akan terus berlanjut hingga pengguna memilih untuk keluar/back. kemudian Inisialisasi Program: Program dimulai dengan memanggil fungsi main() jika program dijalankan sebagai file utama (bukan diimpor sebagai modul/module). juga Program ini memungkinkan user untuk mengelola daftar part racing, serta sebagai Administrator yang dapat mengubah daftar, atau sebagai Buyer yang dapat melakukan transaksi pembelian. Semua data part racing disimpan dalam variabel "daftar_part" dan ditampilkan dalam format yang mudah dibaca menggunakan modul PrettyTable : ) .
