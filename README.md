# Modul-6


## Polishing

setelah implementasi banyak mekanik dari game kita, maka saat nya masuk ke tahap polishing.

tahap polishing yang paling dominan biasanya adalah memasukan asset dan menambahkan animasi pada game :D 

### cara import sprite untuk pixel art

1. pilih gambar asset
2. masukan gambar asset ke dalam folder Sprites
3. klik gambar yang sudah di import
4. ganti pixel per unit menjadi 32
5. ganti filter mode menjadi "point (no filter)"
6. dan compression menjadi none
7. kemudian tekan apply

### cara memasukan gambar kedalam gameObject

untuk yang contoh kali ini akan menggunakan bullet sebagai contoh step nya.

1. double click prefab bullet
2. drag and drop gambar bullet yang sudah di import kedalam sprite renderer
3. ganti color menjadi putih 
4. sesuaikan ukuran sprite (biasa nya agak rusak scale nya jadi bisa di sesuaikan sendiri)
5. kemudian coba mainkan, jika dirasa masih kurang pas ukurannya maka bisa disesuaikan lagi
6. jangan lupa untuk melakukan penyesuaiaan collider nya juga, dengan menekan edit collider.

sip kalau sudah disesuaikan berarti tinggal mengimplementasi import sprite dan masukan sprite ke dalam gameObject lainnya.

### animation

konsep dari animasi adalah, ada banyak sprite yang dirender secara bergantian sehingga terlihat seperti bergerak.

#### import sprite sheet

sprite sheet adalah gambar yang panjang dan berisi banyak sprite

1. masukan gambar spritesheet kedalam folder Sprites
2. ganti sprite mode menjadi multiple
3. ganti pixel per unit menjadi 32
4. ganti filter mode menjadi "point (no filter)"
5. ganti compression menjadi none 
6. kemudian tekan Sprite Editor
7. gunakan option slice di kiri atas 
8. kemudian pilih type menjadi grid by cell size
9. atur ukuran menjadi 32
10. lalu slice dan apply pada kanan atas 

#### implement animation

1. pilih gameObject Player
2. klik window Animation, jika tidak ada tekan window > animation > animation
3. kemudian tekan create, dan buat folder baru bernama Animations, dan save as menjadi player.anim
4. lalu akan keluar timeline 
5. ada sprite Player akan ada tombol dropdown 
6. select semua child nya lalu drag ke dalam timeline
7. setelah itu coba tekan play pada animation nya
8. jika terlalu cepat samples nya bisa dikurangi menjadi 8

### set animation transition 

1. tekan tombol window > animation > animator
2. akan terlihat animation tree sbb 
3. klik kanan kemudian create empty state
4. tekan tombol parameters dan tekan tombol tambah
5. lalu pilih yang boolean dengan nama IsWalking
6. kemudian pada new State klik kanan dan make transition
7. drag panah ke arah state player
8. lakukan juga dari state player 
9. tekan panah yang ke arah player 
10. tekan tombol tambah di bagian kanan dan condition nya menjadi Iswalking = true
11. begitu juga di tombol sebaliknya dengan condition nya menjadi Iswalking = false 

### logic animation

1. di dalam script Player.cs diberi attribute private Animator
``` c#
private Animator _animator;
```

2. kemudian di fungsi Start() di inisiasi
``` c#
_animator = GetComponent<Animator>();
```

3. di fungsi update beri logic, jika player bergerak boolean IsMoving menjadi true 
``` c#

if (_rigidbody.velocity.magnitude > 0)
  _animator.SetBool("IsWalking", true);
else
  _animator.SetBool("IsWalking", false);
```
4. kemudian coba play game nya.













