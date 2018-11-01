---
title: duration — Klasa
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
helpviewer_keywords:
- std::chrono [C++], duration
ms.openlocfilehash: 2b710de6275933b5dc05814664caef92cf251da4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568895"
---
# <a name="duration-class"></a>duration — Klasa

Opisuje typ, który przechowuje *przedział czasu*, która jest czasem trwania między dwoma punktami czasu.

## <a name="syntax"></a>Składnia

```cpp
template <class Rep, class Period = ratio<1>>
class duration;
template <class Rep, class Period>
class duration;
template <class Rep, class Period1, class Period2>
class duration <duration<Rep, Period1>, Period2>;
```

## <a name="remarks"></a>Uwagi

Argument szablonu `Rep` opisuje typ, który jest używany do przechowywania liczby taktów zegara w interwale. Argument szablonu `Period` jest egzemplarzem z [współczynnik](../standard-library/ratio.md) , który opisuje wielkość przedziału, który każdy takt reprezentuje.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|DURATION::Period — Typedef|Reprezentuje synonim dla parametru szablonu `Period`.|
|DURATION::Rep — Typedef|Reprezentuje synonim dla parametru szablonu `Rep`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Czas trwania](#duration)|Konstruuje `duration` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Liczba](#count)|Zwraca liczbę taktów zegara w odstępie czasu.|
|[max](#max)|Statyczne. Zwraca maksymalną dozwoloną wartość parametru szablonu `Ref`.|
|[min](#min)|Statyczne. Zwraca najniższą dozwoloną wartość parametru szablonu `Ref`.|
|[zero](#zero)|Statyczne. W efekcie zwraca `Rep`(0).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[DURATION::operator-](#operator-)|Zwraca kopię obiektu `duration` obiektu wraz z liczbą cykli zanegowanych.|
|[DURATION::operator--](#operator--)|Dekrementuje przechowywanych cykli.|
|[DURATION::operator =](#op_eq)|Zmniejsza liczbę cykli przechowywanych modulo określonej wartości.|
|[DURATION::operator * =](#op_star_eq)|Mnoży liczbę przechowywanych cykli przez określoną wartość.|
|[DURATION::operator / =](#op_div_eq)|Dzieli liczbę przechowywanych cykli przez liczbę cykli określonego `duration` obiektu.|
|[DURATION::operator +](#op_add)|Zwraca `*this`.|
|[DURATION::operator ++](#op_add_add)|Zwiększa liczbę przechowywanych cykli.|
|[DURATION::operator +=](#op_add_eq)|Dodaje liczbę taktów określonego `duration` obiektu do liczby przechowywanych taktów.|
|[DURATION::operator-=](#operator-_eq)|Odejmuje liczbę taktów określonego `duration` obiektu na podstawie liczby przechowywanych taktów.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono >

**Namespace:** std::chrono

## <a name="count"></a>  DURATION::Count —

Pobiera numer taktów zegara w odstępie czasu.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba taktów zegara w odstępie czasu.

## <a name="duration"></a>  DURATION::duration — Konstruktor

Konstruuje `duration` obiektu.

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);

template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>Parametry

*Rep2*<br/>
Typ arytmetyczny do reprezentowania liczby taktów.

*Period2*<br/>
A `std::ratio` specjalizacja szablonu do reprezentowania okresu taktu w jednostkach czasu w sekundach.

*R*<br/>
Liczba impulsów domyślny okres.

*Czas trwania*<br/>
Liczba impulsów okresie zdefiniowanym przez *Period2*.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor konstruuje obiekt, który nie został zainicjowany. Inicjalizacja wartości za pomocą pustych nawiasów klamrowych inicjuje obiekt, który reprezentuje przedział czasu zero taktów zegara.

Drugi, jeden szablon argument Konstruktor konstruuje obiekt, który reprezentuje przedział czasu *R* przy użyciu domyślnego okresu Takty zegara `std::ratio<1>`. Aby uniknąć zaokrąglania liczby osi, to błąd konstruuje obiekt trwania z typu reprezentacji *Rep2* może być traktowana jako zmiennoprzecinkowa wpisz kiedy `duration::rep` nie może być traktowany jako typ zmiennoprzecinkowy.

Trzeci, dwa konstruktora argumentów szablonu konstruuje obiekt, który reprezentuje przedział czasu, którego długość jest przedziałem czasu, który jest określony przez *czas trwania*. Aby uniknąć liczenia taktów, to błąd konstruuje obiekt trwania z innego obiektu czasu trwania, którego typem jest *niewspółmierny* z typem docelowym.

Typu czasu trwania `D1` jest *niewspółmierny* z innym typem czasu trwania `D2` Jeśli `D2` nie może być traktowany jako typ zmiennoprzecinkowy i [ratio_divide\<D1::period, D2:: okres >:: type::den](../standard-library/ratio.md) nie jest 1.

Chyba że *Rep2* jest niejawnie konwertowany na `rep` i `treat_as_floating_point<rep>` *prawdziwe* lub `treat_as_floating_point<Rep2>` *fałszywy*, drugi Konstruktor nie uczestniczy w przeciążeniu rozdzielczości. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

O ile nie przepełnienia jest wywołane podczas konwersji i `treat_as_floating_point<rep>` *prawdziwe*, i / lub `ratio_divide<Period2, period>::den` jest równa 1 oraz `treat_as_floating_point<Rep2>` *fałszywy*, trzeci Konstruktor nie uczestniczy w Rozpoznanie przeciążenia. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

## <a name="max"></a>  DURATION::Max —

Metoda statyczna zwraca górną granicę wartości typu typu parametru szablonu `Ref`.

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca `duration(duration_values<rep>::max())`.

## <a name="min"></a>  DURATION::min —

Metoda statyczna zwraca dolną granicę wartości typu typu parametru szablonu `Ref`.

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca `duration(duration_values<rep>::min())`.

## <a name="duration__operator-"></a>  DURATION::operator-

Zwraca kopię obiektu `duration` obiektu wraz z liczbą cykli zanegowanych.

```cpp
constexpr duration operator-() const;
```

## <a name="duration__operator--"></a>  DURATION::operator--

Dekrementuje przechowywanych cykli.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza metoda zwraca `*this`.

Druga metoda zwraca kopię obiektu `*this` która została dokonana przed dekrementacji.

## <a name="op_eq"></a>  DURATION::operator =

Zmniejsza liczbę cykli przechowywanych modulo określonej wartości.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

*Div*<br/>
W przypadku pierwszej metody *Div* reprezentuje liczbę cykli. W przypadku drugiej metody *Div* jest `duration` obiekt, który zawiera liczbę cykli.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiektu po operacji modułowej.

## <a name="op_star_eq"></a>  DURATION::operator * =

Mnoży liczbę przechowywanych cykli przez określoną wartość.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Parametry

*Iloczyn*<br/>
Wartość typu, który jest określony przez `duration::rep`.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiektu po wykonaniu mnożenia.

## <a name="op_div_eq"></a>  DURATION::operator / =

Dzieli liczbę przechowywanych cykli przez określoną wartość.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Parametry

*Div*<br/>
Wartość typu, który jest określony przez `duration::rep`.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiektu po wykonaniu dzielenia.

## <a name="op_add"></a>  DURATION::operator +

Zwraca `*this`.

```cpp
constexpr duration operator+() const;
```

## <a name="op_add_add"></a>  DURATION::operator ++

Zwiększa liczbę przechowywanych cykli.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza metoda zwraca `*this`.

Druga metoda zwraca kopię obiektu `*this` która została dokonana przed wartością przyrostu.

## <a name="op_add_eq"></a>  DURATION::operator +=

Dodaje liczbę taktów określonego `duration` obiektu do liczby przechowywanych taktów.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Element `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiektu po wykonaniu dodawania.

## <a name="duration__operator-_eq"></a>  DURATION::operator-=

Odejmuje liczbę taktów określonego `duration` obiektu na podstawie liczby przechowywanych taktów.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Element `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiektu po wykonaniu odejmowania.

## <a name="zero"></a>  DURATION::zero

Zwraca `duration(duration_values<rep>::zero())`.

```cpp
static constexpr duration zero();
```

## <a name="op_mod_eq"></a>  DURATION::operator mod =

Zmniejsza liczbę cykli przechowywanych modulo Div lub Div.count().

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

*Div*<br/>
Dzielnik obiektu czasu trwania lub wartość, która reprezentuje liczby cykli.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zmniejsza liczbę cykli przechowywanych modulo dziel i zwraca * to. Funkcja drugiego członka zmniejsza liczbę cykli przechowywanych modulo Div.count() i zwraca \*to.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[duration_values, struktura](../standard-library/duration-values-structure.md)<br/>
