
## Laporan Praktikum

|  | Pemrograman Berbasis Framework 2025 |
|--|--|
| NIM |  2241720185 |
| Nama |  Mochammad Nizar Mahi |
| Kelas | TI - 3B |

# React JS

## Langkah-langkah Praktikum

### 1. Persiapan Lingkungan 

### 2. Membuat Komponen React
```js
import './App.css';

function Header() {
  return (
    <header>
      <h1>Aplikasi React Saya</h1>
    </header>
  );
}

function Main() {
  return (
    <main>
      <h2>Selamat datang di Aplikasi React Saya!</h2>
      <p>Ini adalah area konten utama</p>
    </main>
  );
}

function Footer() {
  return (
    <footer>
      <p>&copy; 2025 Aplikasi React Saya</p>
    </footer>
  );
}

function App() {
  return (
    <div>
      <Header/>
      <Main/>
      <Footer/>
    </div>
  );
}

export default App;
```
Dengan hasil perubahan
![](/praktikum-react/assets/Langkah2.png)
### 3. Menggunakan JSX untuk Membuat Komponen Dinamis
File Counter.js
```js
import React, { useState } from 'react';

function Counter() {
    const [count, setCount] = useState(0);

    function handleClick() {
        setCount(count + 69);
    }

    return (
        <div>
            <p>Hitungan: {count}</p>
            <button onClick={handleClick}>Tambah</button>
        </div>
    );
}

export default Counter;
```
#### Hasil Tampilan 

![](/praktikum-react/assets/Langkah3.png)

### 4. Menggunakan Props untuk Mengirim Data
File Greeting.js
```js 
function Greeting(props) {
    return <h1>Halo, {props.nama}!</h1>;
}

export default Greeting;
```
#### Hasil Tampilan 

![](/praktikum-react/assets/Langkah4.png)

### 5. Menggunakan State untuk Mengelola Data
Modifikasi App.js
```js
function Example(){
  const [name, setName] = useState('John Doe');
  const [age, setAge] = useState(0);
  const [email, setEmail] = useState('');

  const handleNameChange = (e) => {
    setName(e.target.value);
  }
  
  const handleAgeChange = (e) => {
    setAge(e.target.value);
  }
  
  const handleEmailChange = (e) => {
    setEmail(e.target.value);
  }

  return (
    <div>
      <input type='text' placeholder='Name' value={name} onChange={handleNameChange}/>
      <input type='number' placeholder='Umur' value={age} onChange={handleAgeChange}/>
      <input type='email' placeholder='Email' value={email} onChange={handleEmailChange}/>

      <p>{name} berumur {age} tahun dan emailnya adalah {email}</p>
    </div>
  )
}
```
#### Hasil Tampilan
![](/praktikum-react/assets/Langkah5.png)

## Tugas 
### 1. Buat komponen baru bernama TodoList yang menampilkan daftar tugas (todo list). Gunakan state untuk mengelola daftar tugas dan props untuk mengirim dara tugas ke komponen anak.
### 2. Tambahkan fitur untuk menambahkan tugas baru ke dalam daftar menggunakan form input.
### 3. Implementasikan fitur untuk menghapus tugas dari daftar.

### Jawab : 
#### Buat komponen TodoList.js dengan isi file seperti berikut.
```js
import { useState } from "react";

export default function TodoList() {
  const [tasks, setTasks] = useState([]);
  const [newTask, setNewTask] = useState("");

  const addTask = () => {
    if (newTask.trim() !== "") {
      setTasks([...tasks, newTask]);
      setNewTask("");
    }
  };

  const removeTask = (index) => {
    setTasks(tasks.filter((_, i) => i !== index));
  };

  return (
    <div className="max-w-md mx-auto mt-10 p-4 bg-white shadow-lg rounded-xl">
      <h2 className="text-xl font-bold mb-4">Todo List</h2>
      <div className="flex gap-2 mb-4">
        <input 
          type="text" 
          value={newTask} 
          onChange={(e) => setNewTask(e.target.value)} 
          placeholder="Tambahkan tugas baru" 
          className="border p-2 rounded w-full"
        />
        <button onClick={addTask} className="bg-blue-500 text-white p-2 rounded">Tambah</button>
      </div>
      <div>
        {tasks.map((task, index) => (
          <div key={index} className="mb-2 flex justify-between items-center p-3 border rounded">
            <span>{task}</span>
            <button onClick={() => removeTask(index)} className="bg-red-500 text-white p-2 rounded">Hapus</button>
          </div>
        ))}
      </div>
    </div>
  );
}
```
Dan ini adalah hasil dari tampilan nya
![Todo List](/praktikum-react/assets/Tugas.png)
