# Skin segmentation

Ten projekt realizowany jest w ramach pracy magisterskiej i dotyczy automatycznej segmentacji obszarów skóry widocznych na zdjęciach medycznych, z wykorzystaniem danych multimodalnych oraz sieci neuronowych typu U-Net.

---

##  Cel projektu

Celem eksperymentu jest wytrenowanie zestawu modeli U-Net do segmentacji obszarów skóry widocznych gołym okiem na zdjęciach medycznych, które zawierają zarówno obraz RGB, jak i komponent termalny. Następnie wyniki wszystkich modeli zostaną połączone w procesie agregacji predykcji, w którym wspólne decyzje większości sieci zostaną uznane za końcowy wynik segmentacji (ensemble voting).

---

##  Dane wejściowe

- **Obraz wejściowy:**  
  - 4-kanałowe obrazy: klasyczne RGB (3 kanały) + kanał termalny (1 kanał)
- **Etykieta (ground truth):**  
  - Binarna maska segmentacyjna – piksele 1 oznaczają widoczną skórę, 0 – tło

---

##  Architektura modelu

- Model bazowy: **U-Net** (klasyczna architektura segmentacyjna)
- Modyfikacja: obsługa wejścia 4-kanałowego (RGB + termalny)

---

##  Proces uczenia i ewaluacji

- Dane są dzielone przy użyciu **cross-walidacji (10-fold)**.
- Dla każdego folda trenowana jest osobna sieć U-Net.
- W sumie powstaje **10 niezależnych modeli**.
- Podczas predykcji każda sieć generuje własną maskę.
- Końcowy wynik uzyskiwany jest przez **agregację predykcji**:  
  piksel zostaje oznaczony jako „skóra”, jeśli większość (≥6/10) modeli go wskazuje.

---

##  Technologie

- Matlab

---

##  Metryki oceny

- Dice coefficient
- IoU (Intersection over Union)
- Dokładność (Accuracy)
- Wyniki porównywane dla każdego folda oraz agregowanego modelu

---

##  Status projektu

Projekt w toku – obecnie realizowane:
- trening modeli w cross-walidacji
- eksperyment z agregacją predykcji (ensemble voting)

---

