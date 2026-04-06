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