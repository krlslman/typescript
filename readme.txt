Dersler
https://www.youtube.com/watch?v=iTZ1-85I77c&list=PL4cUxeGkcC9gUgr39Q_yD6v-bSyMwKPUI&index=2

Dosyalar:
https://github.com/iamshaunjp/typescript-tutorial/tree/lesson-2

Ders 4: [type]
- Bir array'de bulunmayan bir type'a ait bir öğeyi push edemezsin.
- Bir objenin bir value'sunu farklı tipte değere değiştiremezsin.

Ders 5: [explicit types, union types]
- Değişkeni "let myvariable: boolean" şeklinde tanımlayarak 
    'explicit type' verebilirsin. Bu sayede farklı bir type'da değer alamaz.
- "let myarray: string[]" yazdığımda 'gelecekte string değerler tanımlayabilirim' 
    anlamına gelir fakat içerisinde henüz string öğe tanımlanmadığı için push metodu
    kullanamam. Bunun için "let myarray: string[] = []" şeklinde boş array atanmalı.
- Birden fazla type'ta öğeyi bir array'e eklemek üzere bir array tanımlayalım.
    let myarray: (string|number|boolean)[]=[];
- Birden fazla type'da değer alabilen bir değişken tanımlamak
    let normalVar: string|boolean;
- let ninjaTwo: {
    name: string,
    age: number,
    beltColour: string
    }
    
    ninjaTwo = { name: 'mario', age: 20, beltColour : "black "}

Ders 6:  [any]
- any kullanarak bu type değişim kısıtlamasını kaldırabiliriz
    let age: any = 25;
    ninjaTwo:  { name: any, age: any }  
    (Burada dikkat edelim, kısıt tanımlarken iki nokta, 
        değişkene değer verirken eşittir kullanıyoruz.)

Ders 7:  [public, src, tsconfig.json, include ]
- public klasörü : html, js, css
- src klasörü : server'a deploy etmek istemediğimiz dosyalar, TS
- "tsc src/sandbox.ts" komutu ts'nin yanına js'sini oluşturuyor.
    Fakat bu karışıklığı önleyip ayrı klasöre çıkarmasını sağlayalım.
    "tsc --init" ile tsconfig.json oluşturduk.
    * İçerisinde "rootDir" i un-comment edip değerini "./src" yaptık.
      İçerisinde "outDir" i un-comment edip değerini "./public" yaptık.
      Yani rootDir'den okuduğu ts dosyalarının js'lerini outDir'e çıkaracak.
    * Hata alıyorsan git init ettiğin klasörün içinde alt klasörler içinde çalıştığın için olabilir bu durumda tüm alt klasörlerinde aynı yapıya (src-public) uygun structured olması lazım.
    * Src klasörü dışındaki ts dosyalarının compile edilmesini istemiyorsak tsconfig.json'a "include": ["src"] ekliyoruz.

    In my case it was being ignored because I had noEmit: true in tsconfig.json. For whatever reason, the files still were emitted, but in the same directory instead of following outDir.
    The config file was read correctly and this error also appeared when using the flag.    


Ders 8:  [funtion default and optional value, return colon] 
    * optional parameter sembolü "?",
    * return edilcek değerin type'nı belirleme sembolü ":", (nadir durumlarda gerekebilir fakat genelde kullanmayız çünkü zaten return edilmiş olur)
    * "void" fonksiyonun bir result değeri olmaması anlamına geliyor. Js'te dahilidir ve fonksiyon return etmezse undefined gelir. Fakat Ts'de ayrılmıştır.