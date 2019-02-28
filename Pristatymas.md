<!-- $theme: gaia -->

Std::chrono Calendar
===
![alt-text](https://michelzbinden.com/images/2019/vi/en/calendar-february-2019-uk.jpg)
<small>Mindaugas Kasiulis</small>

---

# Kur, kada, kas 'paveža'?
- *ISO komiteto susirinkimas Jacksonvilyje*
- 2018-03-16 kartu su pasiūlymu nr D0355R7:Extending < chrono > to Calendars and Time Zones
- Clang 7, [Wandbox.org](https://wandbox.org/)

---

# Calendar įnešamos naujovės

---

# last_spec

Tuščio tag'o tipas, kurį naudojant kartu su kitais calendar tipais bus nurodomas paskutinis elementas tam tikroje sekoje.Priklausomai nuo konteksto last_spec gali nurodyti paskutinę mėnesio dieną pvz ```2018y/February/last``` (2018-02-28) ar net paskutinioji tam tikros savaitės dienos pozicija mėnesyje ```2018/February/Sunday[last]```(2018-02-25).
```console
struct last_spec
{
    explicit last_spec() = default;
};
inline constexpr last_spec last{};
```
---

# day

Klasė, kuri atvaizduoja tam tikrą mėnesio dieną. Įprastas reikšmių intervalas [1, 31] bet gali įgyti ir reikšmes iš intervalo [0, 255].

---

# month

Klasė, kuri atvaizduoja tam tikrą metų mėnesį. Kiekvienam mėnesiui ```std::chrono``` namespace iš anksto priskirta po vieną atitinkamai pavadinta konstanta. Įprastas intervalas [1, 12] bet gali saugoti reikšmes [0, 255].

---

# year

Klasė, kuri atvaizduoja tam tikrus metus iš proleptinio (praplėsto) Grigališkojo kalendoriaus. Gali įgyti reikšmes iš intervalo [-32767, 32767].Be bendrų funkcijų galima patikrinti ar saugoma reikšmė atitinka keliamuosius metus:
```console
constexpr bool is_leap() const noexcept;
```
---

# weekday

Klasė, kuri atvaizduoja tam tikrą savaitės dieną iš Grigališkojo kalendoriaus. Įprastas reikšmių intervalas - [0, 6] 
bet gali įgytį reikšmes ir iš intervalo [0, 255].Kiekvienai savaitės dienai std::chrono namespace iš anksto priskirta po vieną atitinkamai pavadintą konstantą.

---

# Bendros funkcijos
- Padidinti/pamažinti:
```console
constexpr std::chrono::day& operator++() noexcept;)
constexpr std::chrono::day operator++(int) noexcept;
constexpr std::chrono::day& operator--() noexcept;
constexpr std::chrono::day operator--(int) noexcept;
```
- Patikrinti ar saugoma reikšmė yra įprasto intervalo ribose
``` console
constexpr bool ok() const noexcept;
```
ir dar daug kitų...

---

# weekday_indexed ir weekday_last

Klasė ```weekday_indexed``` surišą tam atitinkamą savaitės dieną su indeksu n iš intervalo [1, 5]. Atitinka pirmą, antrą, trečią, ketvirtą ir penktą kokio nors mėnesio dieną. Per funkcijas ```weekday()``` ir ```index()``` galima prieti prie saugomų savaitės dienos ir indekso reikšmių. Klasė ```weekday_last``` atvaizduoja paskutinę savaitės dieną mėnesyje.

---

# month_day ir month_day_last

Klasė ```month_day``` atvaizduoja dar kol kas nenurodytų metų nurodyto mėnesio nurodytą dieną. Per funkcijas ```month()``` ir ```day()``` prieiname prie saugomų mėnesio ir dienos reikšmių. Klasė ```month_day_last``` atitinkamai atvaizduoja šio mėnesio paskutinę dieną.

---

# month_weekday ir month_weekday_last

Klasė ```month_weekday``` atvaizduoją dar nenurodytų metų nurodyto mėnesio n-tają savaitės dieną. Funkcijomis ```month()``` ir ```weekday_indexed()``` prieinama prie saugomų reikšmių. Atitinkamai, klasė ```month_weekday_last``` nurodo šio mėnesio paskutinią savaitės dieną.

---

# year_month

Klasė, kuri atvaizduoja nurodytų metų nurodytą mėnesį.Per funkcijas ```year()``` ir ```month()``` galime prieiti prie saugomų reikšmių.Jas modifikuoti galima per ```+= ir -=``` operatorius.

---

# year_month_day ir year_month_day_last

Klasė ```year_month_day``` atvaizduoja nurodytus metus, mėnesį ir dieną.Per funkcijas ```year(), month(), day()``` prieinama prie saugomų reikšmių.Reikšmės keičiamos naudojant operatorius ``` += ir -=```, galima konvertuoti į ```std::chrono::timepoint``` naudojant operatorius ``` sys_days, local_days```. Klasė ```year_month_last``` atvaizduoja nurodytų metų mėnesio paskutinę dieną.

---

# year_month_weekday ir year_month_weekday_last
Realiai viskas identiška su ```year_month_day```, tik vietoje dienos saugoma n-toji savaitės diena. Prisideda funkcijos ```index() ir weekday_indexed```, kuriomis pasiekiamas indeksas ir indeksuota savaitės diena.Klasė ```year_month_weekday_last``` atvaizduoja paskutinę nurodytų metų mėnesio savaitės dieną.

---

# Operator /
Toks vo ![alt-text](http://www.onlinesalesguidetip.com/wp-content/uploads/2014/12/canstockphoto7743917-300x285.jpg.jpg) 
kad nusipelnė atskiros skaidės. Galima naudoti su visomis iki šiol išvardintomis klasėmis.```Operator /``` overload'ai suteikia tradicinę Grigališko kalendoriaus sintaksę, pvz ```year/month/weekday[i]``` ar ```1999y/10/08```

---

# Šioks toks pavyzdys

[opa](https://wandbox.org/permlink/vqwMyTphHJv5iXX7)

---

# Ačiū už jūsų dėmesį 

![alt-text](
https://images-cdn.9gag.com/photo/av8o7XX_700b.jpg)

