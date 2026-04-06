# EnesTahaKayacanRollABallGame
# Roll-a-Ball Game - Enes Taha Kayacan

## 1. Setting Up the Game (Oyunun Kurulumu)
* **Steps:** Created the Ground (Plane) and the Player (Sphere). Organized the project folders as 'Materials', 'Scripts', and 'Scenes'.
* **What I Learned:** I learned how to manage a Unity project and how to use materials to color objects.
* **Errors & Fixes:** - **Error:** At first, GitHub Desktop tried to upload 2800 files.
    - **Fix:** I realized the `.gitignore` file was in the wrong folder. I moved it to the root of the Unity project, and the file count dropped to 66.

## 2. Moving the Player (Oyuncunun Hareketi)
* **Steps:** Added a **Rigidbody** component to the Player. Created a C# script named `PlayerController`.
* **What I Learned:** I learned how to use Unity's Physics system and how to read player input.

## 3. Moving the Camera (Kameranın Hareketi)
* **Steps:** Main Camera için `CameraController` adında bir script oluşturdum. Kamerayı oyuncunun (Player) içine atmak yerine, aradaki mesafeyi (offset) hesaplayan bir kod yazdım.
* **What I Learned:** `Update` ve `LateUpdate` arasındaki farkı öğrendim. Kamerayı `LateUpdate` içinde hareket ettirmenin, oyuncu hareket ettikten sonra kameranın konumunu güncellediği için daha sarsıntısız (smooth) bir görüntü sunduğunu fark ettim.
* **Errors & Fixes:**
    - **Error:** Kamerayı doğrudan Player objesinin içine (child) sürüklediğimde, top her döndüğünde kamera da topun etrafında dönmeye başladı ve görüntü bozuldu.
    - **Fix:** Kamerayı Player'ın içinden çıkardım ve script yardımıyla oyuncu ile kamera arasındaki mesafeyi sabitleyerek (offset) sorunu çözdüm.

## 4. Setting Up the Play Area (Oyun Alanının Kurulması)
* **Steps:** Oyun alanının etrafına topun dışarı düşmesini engelleyecek duvarlar (North, South, East, West Walls) ekledim. Tüm duvarları hiyerarşide düzenli durması için "Walls" adında boş bir GameObject'in (Empty Parent) altına topladım.
* **What I Learned:** "Parent-Child" (Ebeveyn-Çocuk) ilişkisini ve hiyerarşiyi düzenli tutmanın önemini öğrendim. Ayrıca objeleri sahnede hızlıca hizalamak için "Transform" değerlerini manuel olarak ayarlamayı pratik ettim.
* **Errors & Fixes:**
    - **Error:** Duvarları tek tek oluşturduğumda hiyerarşi çok kalabalık ve karışık göründü.
    - **Fix:** Bir "Empty GameObject" oluşturup tüm duvarları onun içine sürükledim. Böylece hiyerarşiyi hocanın istediği gibi tertemiz ve organize bir hale getirdim.

    ## 5. Creating Collectibles (Toplanabilir Objelerin Oluşturulması)
* **Steps:** Oyuncunun toplayacağı küpleri oluşturdum ve bunlara kendi etrafında dönmelerini sağlayan bir `Rotator` script'i yazdım. Objeleri daha kolay yönetmek için **Prefab** sistemini kullandım.
* **What I Learned:** Prefab sisteminin, bir objenin kopyalarını (instance) tek bir merkezden yönetmek için ne kadar güçlü olduğunu öğrendim.

## 6. Detecting Collisions (Çarpışmaları Algılama)
* **Steps:** PlayerController script'i içine `OnTriggerEnter` fonksiyonunu ekledim. Oyuncu "Pick Up" etiketine (tag) sahip bir objeye çarptığında, o objenin pasif hale gelmesini (`SetActive(false)`) sağladım.
* **What I Learned:** `OnCollisionEnter` (fiziksel çarpışma) ve `OnTriggerEnter` (içinden geçme) arasındaki farkı öğrendim. Tetikleyicilerin (Triggers) fiziksel bir tepki vermeden sadece bir olayı başlatmak için kullanıldığını kavradım.
* **Errors & Fixes:**
    - **Error:** Oyuncu küplere çarptığında küpler kaybolmuyor, aksine oyuncuyu geri itiyordu.
    - **Fix:** Collectible objelerinin (Pick Up) üzerindeki Box Collider bileşeninde "Is Trigger" kutucuğunun işaretli olması gerektiğini fark ettim. Ayrıca script içinde "Pick Up" etiketinin büyük/küçük harf duyarlı olduğunu (Case-sensitive) öğrendim.

## 7. Displaying the Score and Text (Puanın Görüntülenmesi)
* **Steps:** Hiyerarşide bir **UI > Text - TextMeshPro** objesi oluşturdum. `PlayerController` scripti içinde `count` adında bir değişken tanımladım ve her obje toplandığında bu değeri artırıp ekrana yazdırdım.
* **What I Learned:** Unity'de UI (Kullanıcı Arayüzü) sisteminin 3D dünyadan farklı bir katmanda (Canvas) çalıştığını öğrendim. **TextMeshPro** kütüphanesini projeye dahil etmeyi ve kod içinde `using TMPro;` ad alanını (namespace) kullanmayı kavradım.
* **Errors & Fixes:**
    - **Error:** Kod yazarken `TextMeshProUGUI` tipini kullandığımda hata aldım.
    - **Fix:** Script'in en üstüne `using TMPro;` satırını eklemeyi unuttuğumu fark ettim. Ayrıca ilk başta Text ekranda gözükmedi; Canvas ayarlarından "UI Scale Mode" kısmını "Scale With Screen Size" yaparak farklı çözünürlüklerde görünür olmasını sağladım.

## 8. Adding AI Navigation (Yapay Zeka Navigasyonu)
* **Steps:** Sahneye bir düşman (Enemy) objesi ekledim ve buna **NavMesh Agent** bileşeni atadım. Zemini (Ground) navigasyon alanı olarak belirlemek için **NavMesh Surface** kullanarak "Bake" işlemini gerçekleştirdim. Düşmanın oyuncuyu takip etmesi için basit bir C# takip script'i yazdım.
* **What I Learned:** Unity'nin NavMesh sistemini kullanarak bir objeye "yol bulma" (pathfinding) yeteneği kazandırmayı öğrendim. Dinamik ve statik objelerin navigasyon üzerindeki etkilerini kavradım.


