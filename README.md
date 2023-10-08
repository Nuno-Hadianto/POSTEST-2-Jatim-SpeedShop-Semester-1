Jatim SpeedShop Application (flowchart masih progress...)

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

** Output Program **

![1](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/67d8f0a2-9945-42e3-8afb-93d61b89c311)

![2](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/5fb5f7fc-1785-4747-89c6-501cfd960fd2)

![3](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/208fd920-d079-43b9-9b59-714716f71688)

![4](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/8b5f41f2-065c-4a2e-a909-bda64c4b9e1e)

![5](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/3ca12a61-dfe4-48b6-84b9-8ae710e5f694)

![6](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/379f041f-2b17-47c9-a16d-6c2170f6bbd5)

![7](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/330ed9a1-332b-4868-b5ec-fd30ecee6dea)

![8](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/0a90de86-05b7-4ba0-ade2-755b50fec17d)

![9](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/1fe39ebb-3717-4341-92cc-854ddbdd3808)

![10](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/699556f5-2e6a-4ce0-9548-713d44920e53)

![11](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/0827918e-a7fc-4995-86ab-f9f43265651d)

![12](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/33c3d6ba-cc4f-47bd-81cb-b66c155b8ab1)

![13](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/11fbc58e-8a5f-4c9c-87d3-a2e5bb4078b0)

![14](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/a2fa9249-e01b-4677-af0f-142aedf4f4e1)

![15](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/e7f7c4ac-bb17-46d8-bc75-ceeeb437d827)

![16](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/7e360bc4-dbf0-4bd3-964b-170028ebb0f2)

![17](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/250cb399-83c3-4e4b-b5a3-dff86b84dbda)

![18](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/5946475b-72cc-460e-8891-a4317f10f8db)

![19](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/bab70652-5cc1-4640-af8d-f46f47751b8f)

![20](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/e4a6a089-c0c0-4fd2-a32f-d26f583e2122)

![21](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/d28b3755-6256-4ec2-8728-0667615f3a4d)

![22](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/7da9b722-7001-458f-95a2-0ec181b25ba9)

![23](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/19060906-8a7b-4c59-942a-5f924049e17f)

** Flowchart **

![flowchart pos tes 2 drawio](https://github.com/Nuno-Hadianto/POSTEST-2-Jatim-SpeedShop/assets/63713816/5d72eb11-f29d-4f78-a55a-544964120b39)

