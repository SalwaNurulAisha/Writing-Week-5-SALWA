### REACT JS

- **React** ini merupakan sekumpulan kode javascript yang dapat digunakan untuk membuat user interface website.
- **Kelebihan React**

  - membuat aplikasi berjalan lebih cepat meskipun data banyak (_fast_).
  - membuat 1 halaman memiliki beberapa kumpulan file js (_Modular_).
  - dapat digunakan pada aplikasi berskala kecil hingga kompleks (_scalable_).
  - banyak digunakan (_popular_).

- **Cara Menggunakan React**

  > 1. Install node.js, dan pastikan sudah berhasil terinstal atau belum dengan menggunakan command 'node -v'.
  > 2. buat library :arrow_right: **npx create-react-app name-react**
  > 3. masuk ke posisi folder :arrow_right: **cd name-folder**
  > 4. untuk membuka folder pada vscode masukan command :arrow_right: **code .**
  > 5. untuk menjalankan react :arrow_right: **npm run start**

- **Flow Menggunakan React**
  - **html** pada folder public
  - **index.js** pada folder src untuk penggunaan konfigurasi.
  - **App.js** folder src, akan banyak digunakan untuk memasukkan codingan.

* **JSX (JAVASCRIPT XML)** :arrow_right: HTML yang berada dalam sebuah fungsi javascript, hal ini bisa digunakan pada react.
* **Rules Penggunaan JSx**

  - hanya boleh memiliki 1 parent element, jika ingin lebih bisa dibungkus menggunakan
    > tag div atau <></>
  - menggunakan attribut **className** di tag element HTML nya, bukan **class** aja.

* untuk membuat syntax jsx agar lebih cepat menggunakan keyword :arrow_right:

  - **rfce** => penulisan function biasa

    ```jsx
    import React from "react";

    function conditional() {
      return <div>conditional</div>;
    }

    export default conditional;
    ```

  - **rafce** => penulisan dengan arrow function

    ```jsx
    import React from "react";

    const conditional = () => {
      return <div>conditional</div>;
    };

    export default conditional;
    ```

* tempat untuk mendeklarasikan JS (variabel) yaitu **"sebelum return"**

* **Conditional in JSX** satu-satunya yg bisa digunakan yaitu ternary operator
  ```js
  {
    isLogin ? <p>sudah login</p> : <p>belum login</p>;
  }
  ```
* **Looping in JSX**
  menggunakan maping. contoh :arrow_down:
  maping menampilkan array of object

```js
const App = () => {
  const data = ["salwa", "miana"];

  return (
    {data.map((item, key) => (
          <h1 key={key}>{item}</h1>
        ))}
  )
}
```

### REACT JS - COMPONENTS

- React JS memiliki sifat component-based
  - bisa membuat komponen sekecil apapun dan didalamnya terdapat hal sespesifik mungkin.
  - satu komponen bisa digunakan di banyak tempat dan reusable (dipakai kembali).

* **props** : merupakan properti untuk mempasing bentuk sebuah data yang akan disesuaikan dengan nama / kebutuhan. misal :

  > Data (attribute) yang akan dipasing berada pada file _Course.js_

  ```js
  <CourseCard.js title="how to be programming" detail="Tips and trick menjadi programming" />
  ```

  > props nya akan dimasukan ke dalam file _CourseCard.js_
  >
  > - **_props_** dimasukkan ke function dan juga parameternya.

  ```js
  const CourseCard = (props) => {
    return (
      <div>
        <h1>{props.title}</h1>
        <p>{props.detail}</p>
      </div>
    );
  };

  export default CourseCard;
  ```

  > - **penulisan Props destructure** : proses yg langsung mengambil data / nama properti yg ada di dalam props nya dan diletakkan langsung dalam function

  ```js
  const CartItem = ({ product }) => {
    return (
      <div>
        <h1>{product}</h1>
      </div>
    );
  };

  export default CartItem;
  ```

### REACT STATE

- data yang berkemungkinan berubah pada suatu komponen.
- **useState** :arrow_right: fitur untuk membuat state dalam functional component.
- Cara Penggunaan useState
  1. mengimport useState dari react.
  ```js
  import { useState } from "react";
  ```
  2. menuliskan useState
     > Cara Penulisan useState()
     > ![Cara Menulis State](/assets/penulisan-state.PNG)

> :pushpin: Pengganti variabel di react yaitu menggunakan state.

**Variabel JS biasa** :

```js
const nama = "Salwa";
```

### REACT JS - useEffect

- useEffect ini biasa disebut lifecycle (siklus hidup).
- data yg dideklarasikan pada suatu waktu bisa digunakan, dan pada saat sudah tidak dibutuhkan maka dibuang atau dibuat mati.
- Cara Penggunaan useEffect

  1. import useEffect dari react

     ```js
     import { useEffect } from "react";
     ```

  2. penulisan useEffect : diatas return, dibawah function

     ````js
     function App() {

           useEffect(() => {
             console.log("tes");
           }, []);

           return (
             <div className="App">
             <h1>Use Effect</h1>
             </div>
           );
          }

          export default App;
          ```
     ````

> :pushpin: render pertama akan berjalan 2 kali.

> pada **useEffect** [dependency] : diisi ketika komponen ingin di render ulang.

- cara baca penggunaan useEffect

  1. baca state
  2. baca return
  3. baca useEffect
  4. kembali ke return

* **axios** :

  - untuk menampilkan data API.
  - axios merupakan pengganti fetch.
  - agar dapat digunakan, import axios nya terlebih dahulu dari react.

    ```js
    import { useEffect, useState } from "react";
    import axios from "axios";

    function App() {
      const [dataGithub,setDataGithub] = useState({});

      // useeffect call api
      let url = "https://api.github.com/users/SalwaNurulAisha";

      useEffect(() => {
        async function getAPI() {
          const result = await axios.get(url);
          console.log(result);
          setDataGithub(result.data);
        }

        getAPI();
      }, []);

      console.log(dataGithub);

      return (
        <div className="App">
          <h1>Use Effect</h1>

          {/* useEffect data github  */}
          <h1>Nama github: {dataGithub.name}</h1>
          <h1>Username: {dataGithub.login}</h1>
          <h1>id: {dataGithub.id}</h1>
      );
    }

    export default App;
    ```

### REACT ROUTER DOM

- Cara Penggunaan
  1. install react router
     ```js
     npm install react-router-dom@6
     ```
  2. import react-router dari react
     ```js
     import { BrowserRouter, Routes, Route } from "react-router-dom";
     ```
  3. Flow code-nya :
     a. BrowserRouter
     b. Routes.
     c. Route (single closing </> ) => path & element

* **tempat untuk mendaftar**
  Link : berpindah dari satu halaman ke halaman lain
