# Karta zgłoszenia tematu projektu

**Grupa:** L2 · **Zespół:** Z.. · **Data:** 21.10.2026r.
Sztuczna inteligencja — laboratorium · Collegium Da Vinci · rok akad. 2026/2027
Oddajecie mailem do **22.10, 16:45**, temat `SI L2 · Z4 · karta`.

## 1. Skład zespołu

> Rola jest wstępna — można ją zmienić w trakcie projektu bez uzgadniania.

| Imię i nazwisko | Nr albumu | Rola (wstępna)                               |
|-----------------|-----------|----------------------------------------------|
| Radosław Sieroń | 31092     | Poszukiwanie danych, Dokumentacja, Prezentacja |
| Michał Zarzycki | 31039     | Implementacja kodu, Prezentacja              |
|                 |           |                                              |

## 2. Roboczy tytuł (PL)
Detektor rodzaju pojazdów w ruchu ulicznym
## 3. Tytuł (EN)
Vehicle Type Detector
## 4. Problem — co system ma robić i dla kogo (3–5 zdań)
Zarządcy dróg i samorządy potrzebują dokładnych danych o tym, jakie pojazdy poruszają się po drogach, a ręczne liczenie jest kosztowne i podatne na błędy. Projekt zakłada system automatycznie rozpoznający typ pojazdu z obrazu kamery przy użyciu klasycznego uczenia maszynowego (np. cechy HOG i klasyfikator SVM), który nie wymaga dużych zbiorów danych ani mocnego sprzętu. Zebrane dane mogą wspierać planowanie infrastruktury, sterowanie sygnalizacją i egzekwowanie zakazów wjazdu.
## 5. Technologia SI

- [ ] sieć neuronowa
- [ ] system ekspertowy / wnioskowanie regułowe
- [ ] algorytm genetyczny
- [X] klasyczne uczenie maszynowe

Dlaczego ta technologia pasuje do tego problemu (2–3 zdania):

Klasyczne uczenie maszynowe (np. SVM, Random Forest, k-NN) dobrze pasuje do problemu Vehicle Type Detector, ponieważ klasyfikacja typu pojazdu (osobowy, ciężarowy, motocykl, autobus) opiera się na cechach, które można łatwo wyekstrahować ręcznie: wymiarach, proporcjach sylwetki, histogramach gradientów (HOG) czy liczbie osi. Takie modele działają skutecznie już przy stosunkowo małych zbiorach danych, uczą się szybko i nie wymagają mocnego GPU, co ułatwia wdrożenie, np. na urządzeniach brzegowych przy drogach. Są też bardziej interpretowalne niż sieci głębokie, więc łatwiej wyjaśnić, dlaczego pojazd został przypisany do danej klasy.


## 6. Dane

- Źródło: https://www.kaggle.com/datasets/ahmedhaytham/car-detection
- Rozmiar / format: 416x416 / jpg
- Czy dane są już dostępne? tak / nie — plan pozyskania: tak

## 7. Stos technologiczny
Stos technologiczny: Python z bibliotekami OpenCV i scikit-image (przetwarzanie obrazów, HOG), scikit-learn (model i metryki) oraz Matplotlib (wykresy), w środowisku Jupyter Notebook.
## 8. Kryterium sukcesu

- Metryka i próg: accuracy ≥ 80% i macro F1 ≥ 0,75 na zbiorze testowym, przy recall dla każdej klasy ≥ 0,70.
- Punkt odniesienia (prosta metoda, z którą porównacie wynik): prosty baseline, czyli klasyfikator przewidujący najczęstszą klasę (DummyClassifier), co daje ok. 25–30% accuracy przy 4 klasach, oraz k-NN na surowych pikselach. Model HOG + SVM musi wyraźnie pokonać oba.

## 9. Zakres minimalny (co powstanie na pewno)
Zakres minimalny: klasyfikacja zdjęć do 3–4 typów pojazdów (osobowy, ciężarowy, autobus, motocykl). Projekt obejmuje publiczny zbiór danych, cechy HOG, klasyfikator SVM lub Random Forest, ocenę metrykami (accuracy, F1, macierz pomyłek) oraz prosty skrypt zwracający typ pojazdu dla podanego zdjęcia.
## 10. Zakres opcjonalny (co dorobimy, jeśli starczy czasu)
Poza zakresem: detekcja wielu pojazdów na jednym obrazie, analiza wideo w czasie rzeczywistym, głębokie sieci neuronowe i wdrożenie na urządzenia brzegowe. Te elementy można wymienić jako możliwe rozszerzenia.
## 11. Repozytorium
https://github.com/m-zarzycki/Vehicle-type-detector

(uzupełnicie 22.10)

## 12. Główne ryzyko i plan awaryjny
Ryzyko: niska skuteczność modelu przez zmienne ujęcia i oświetlenie, podobne klasy lub mały zbiór danych.  
Plan awaryjny: augmentacja i zbalansowanie danych, mniej klas, strojenie SVM. W ostateczności cechy z gotowej sieci CNN (np. MobileNet) połączone z klasycznym SVM.
---

*Decyzja prowadzącego:* [ ] zatwierdzony  [ ] do poprawy · *Uwagi:*