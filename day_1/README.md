# 📝 Todo List Sederhana — Vue.js

Proyek ini adalah latihan dasar Vue.js untuk membuat aplikasi **Todo List** dengan fitur lengkap: tambah tugas, tandai selesai, hapus tugas, counter tugas aktif, serta logika otomatis memindahkan tugas yang selesai ke bagian bawah daftar.

Proyek ini menggunakan **Vue 3 Composition API** dan dapat dijalankan dengan cara:

* Menggunakan **Vite + Vue 3 (Single File Component)**

Dokumentasi ini menjelaskan struktur kode, cara kerja, dan konsep Vue yang digunakan.

---

## 🚀 Fitur Utama

* ✔️ Menambahkan task baru
* ✔️ Menandai task sebagai selesai
* ✔️ Menghapus task
* ✔️ Menghitung jumlah task aktif
* ✔️ Memindahkan task yang selesai ke bagian bawah secara otomatis
* ✔️ Validasi input (tidak bisa tambah task kosong)

---

## 📂 Struktur Proyek (Versi Vite)

```
project/
│── index.html
│── package.json
│── vite.config.js
└── src/
    │── main.js
    │── App.vue
    └── components/
        └── TodoList.vue
```

---

## 📌 Penjelasan File & Kode Utama

### 1️⃣ **App.vue**

`App.vue` adalah komponen utama yang hanya bertugas memanggil komponen `TodoList.vue`.

* Merender UI utama
* Menjadi wadah aplikasi
* Pemanggil komponen list tugas

---

### 2️⃣ **TodoList.vue** (Komponen Utama Todo)

Di dalam file inilah semua logika todo list ditulis.

### 🔧 State (Data)

Menggunakan `ref` untuk membuat variabel reaktif:

* `tasks`: menyimpan seluruh daftar task
* `newTask`: menyimpan teks dari input saat user mengetik

### 🧠 Methods Utama

#### **1. addTask()**

Menambah task baru ke dalam list.

* Memastikan input tidak kosong
* Auto-generate ID menggunakan `Date.now()`

#### **2. removeTask(id)**

Menghapus data task berdasarkan ID.

#### **3. toggleTask(id)**

Mengubah status done / belum selesai pada task.

---

### 🔍 Computed Properties

Digunakan untuk menghitung data secara otomatis tanpa mengubah state.

#### **1. activeCount**

Menghitung berapa banyak task yang **belum selesai**.

#### **2. orderedTasks**

Mengatur urutan tampilan task:

* Task belum selesai ditampilkan dulu
* Task selesai pindah otomatis ke bawah

Ini adalah bagian penting dari challenge.

---

## 🧩 Cara Kerja Fitur Utama

### ⭐ 1. Tambah Task

```
state.tasks.push({ id, title, done: false })
```

Task baru otomatis muncul di bagian atas daftar.

---

### ⭐ 2. Tandai Selesai

Saat checkbox diklik, method `toggleTask()` akan membalik nilai `done`.

Karena urutan list dikontrol oleh `orderedTasks`, Vue akan otomatis memindahkan task yang selesai ke bagian bawah.

---

### ⭐ 3. Hapus Task

```
tasks.value.splice(index, 1)
```

Task akan hilang langsung dari daftar.

---

### ⭐ 4. Counter Task Aktif

```
computed(() => tasks.value.filter(t => !t.done).length)
```

Vue akan menghitung ulang setiap kali ada perubahan.

---

## 🖼️ Preview UI (Sederhana)

* Input untuk mengetik task
* Tombol tambah
* Daftar task
* Checkbox untuk selesai / belum
* Tombol hapus
* Counter aktif

---

## 📦 Instalasi (Versi Vite)

```bash
npm install
npm run dev
```

Lalu buka browser ke URL yang muncul.

---

## 🛠️ Konsep Vue Yang Dipelajari

* **v-model** → binding input
* **v-for** → render list
* **v-if** → kondisi tampilan
* **methods** → aksi user seperti tambah/hapus
* **computed** → data turunan (counter & ordering)
* **reactive/ref** → data reaktif
* **event handling (@click, @change, @keyup.enter)**

Sangat cocok sebagai latihan dasar Vue.js!

---

## 🎯 Challenge Lanjutan (Opsional)

* Simpan data ke localStorage
* Edit task
* Tambah filter All / Active / Completed
* Animasi transisi menggunakan `<transition-group>`

---

## 👨‍💻 Author

Project ini dibuat sebagai latihan challenge Vue.js hari pertama.

