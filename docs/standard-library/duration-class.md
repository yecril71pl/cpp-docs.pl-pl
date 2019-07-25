---
title: duration — Klasa
ms.date: 03/27/2016
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
ms.openlocfilehash: 4c537b7dfdd23ba641438e0caf6306cf5549b2d7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454305"
---
# <a name="duration-class"></a>duration — Klasa

Opisuje typ, który zawiera *przedział czasu*, który jest czas, który upłynął między dwoma punktami czasu.

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

Argument `Rep` szablonu opisuje typ, który jest używany do przechowywania liczby taktów zegara w interwale. Argument `Period` szablonu jest wystąpieniem [współczynnika](../standard-library/ratio.md) opisującym rozmiar interwału reprezentowanego przez poszczególne znaczniki.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|czas trwania::p eriod typedef|Reprezentuje synonim dla parametru `Period`szablonu.|
|Duration:: przedstawiciel typedef|Reprezentuje synonim dla parametru `Rep`szablonu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Czas trwania](#duration)|Konstruuje `duration` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[liczbą](#count)|Zwraca liczbę taktów zegara w przedziale czasu.|
|[max](#max)|Ruchom. Zwraca maksymalną dozwoloną wartość parametru `Ref`szablonu.|
|[min](#min)|Ruchom. Zwraca najmniejszą dozwoloną wartość parametru `Ref`szablonu.|
|[zero](#zero)|Ruchom. W efekcie zwraca `Rep`(0).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Duration:: operator-](#operator-)|Zwraca kopię `duration` obiektu wraz z negacją liczby taktów.|
|[Duration:: operator--](#operator--)|Zmniejsza liczbę przechowywanych cykli.|
|[Duration:: operator =](#op_eq)|Zmniejsza liczbę przechowywanych znaczników modulo określoną wartość.|
|[duration::operator*=](#op_star_eq)|Mnoży liczbę przechowywanych cykli przez określoną wartość.|
|[Duration:: operator/=](#op_div_eq)|Dzieli liczbę przechowywanych cykli przez liczbę cykli określonego `duration` obiektu.|
|[Duration:: operator +](#op_add)|Zwraca `*this`wartość.|
|[Duration:: operator + +](#op_add_add)|Zwiększa liczbę przechowywanych cykli.|
|[Duration:: operator + =](#op_add_eq)|Dodaje liczbę cykli określonego `duration` obiektu do liczby przechowywanych cykli.|
|[Duration:: operator-=](#operator-_eq)|Odejmuje liczbę cykli określonego `duration` obiektu od liczby przechowywanych cykli.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<Chrono >

**Przestrzeń nazw:** std:: Chrono

## <a name="count"></a>czas trwania:: Count

Pobiera liczbę taktów zegara w przedziale czasowym.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba taktów zegara w przedziale czasu.

## <a name="duration"></a>czas trwania::d Konstruktor wersja

Konstruuje `duration` obiekt.

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);

template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>Parametry

*Rep2*\
Typ arytmetyczny reprezentujący liczbę taktów.

*Period2*\
Specjalizacja `std::ratio` szablonu reprezentująca okres taktu w jednostkach sekund.

*R*\
Liczba taktów okresu domyślnego.

*Trwania*\
Liczba taktów okresu określonego przez *Period2*.

### <a name="remarks"></a>Uwagi

Konstruktor domyślny konstruuje obiekt, który jest niezainicjowany. Inicjowanie wartości za pomocą pustych nawiasów klamrowych inicjuje obiekt, który reprezentuje przedział czasu równy zero Takty zegara.

Drugi Konstruktor argumentów szablonu konstruuje obiekt, który reprezentuje przedział czasu w Takty *języka R* przy użyciu domyślnego okresu `std::ratio<1>`. Aby uniknąć zaokrąglania liczby taktów, występuje błąd podczas konstruowania obiektu czasu trwania z typu reprezentacji *Rep2* , który może być traktowany jako typ zmiennoprzecinkowy, gdy `duration::rep` nie może być traktowany jako typ zmiennoprzecinkowy.

Trzeci, dwa Konstruktor argumentów szablonu konstruuje obiekt, który reprezentuje przedział czasu, którego długość jest przedział czasu określony przez czas *trwania*. Aby uniknąć obcięcia liczby taktów, występuje błąd podczas konstruowania obiektu czasu trwania z innego obiektu czasu trwania, którego typ jest *niewspółmierny* z typem docelowym.

Typ `D1` czasu trwania jest *niewspółmierny* z innym typem `D2` czasu trwania, jeśli `D2` nie może być traktowany jako typ zmiennoprzecinkowy i [ratio_divide\<D1::p eriod, D2::p eriod >:: Type::d pl](../standard-library/ratio.md) nie jest 1.

O *ile Rep2* nie jest niejawnie konwertowany `treat_as_floating_point<rep>`do `rep` i ma `treat_as_floating_point<Rep2>` *wartość true lub ma* *wartość false*, drugi Konstruktor nie uczestniczy w rozpoznawaniu przeciążenia. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

Chyba że żadne przepełnienie nie jest wywołane `treat_as_floating_point<rep>`w konwersji i *ma wartość true*, lub `treat_as_floating_point<Rep2>`obie `ratio_divide<Period2, period>::den` są równe 1 i ma *wartość false*, trzeci Konstruktor nie uczestniczy w rozpoznawaniu przeciążenia. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

## <a name="max"></a>czas trwania:: max

Metoda statyczna zwracająca górną granicę dla wartości typu `Ref`parametru szablonu.

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca wartość `duration(duration_values<rep>::max())`.

## <a name="min"></a>czas trwania:: min

Metoda statyczna zwracająca dolną granicę dla wartości typu `Ref`parametru szablonu.

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca wartość `duration(duration_values<rep>::min())`.

## <a name="operator-"></a>Duration:: operator-

Zwraca kopię `duration` obiektu wraz z negacją liczby taktów.

```cpp
constexpr duration operator-() const;
```

## <a name="operator--"></a>Duration:: operator--

Zmniejsza liczbę przechowywanych cykli.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza metoda zwraca `*this`.

Druga metoda zwraca kopię `*this` , która jest wykonywana przed zmniejszeniem.

## <a name="op_eq"></a>Duration:: operator =

Zmniejsza liczbę przechowywanych znaczników modulo określoną wartość.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

*Służąc*\
Dla pierwszej metody *DIV* reprezentuje liczbę cykli. Dla drugiej metody *DIV* jest `duration` obiektem, który zawiera liczbę cykli.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiekt po wykonaniu operacji modulo.

## <a name="op_star_eq"></a>Duration:: operator * =

Mnoży liczbę przechowywanych cykli przez określoną wartość.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Parametry

*Iloczyn*\
Wartość typu, który jest określony przez `duration::rep`.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiekt po wykonaniu mnożenia.

## <a name="op_div_eq"></a>Duration:: operator/=

Dzieli liczbę przechowywanych cykli przez określoną wartość.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Parametry

*Służąc*\
Wartość typu, który jest określony przez `duration::rep`.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiekt po wykonaniu dzielenia.

## <a name="op_add"></a>Duration:: operator +

Zwraca `*this`wartość.

```cpp
constexpr duration operator+() const;
```

## <a name="op_add_add"></a>Duration:: operator + +

Zwiększa liczbę przechowywanych cykli.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza metoda zwraca `*this`.

Druga metoda zwraca kopię `*this` , która jest wykonywana przed przyrostem.

## <a name="op_add_eq"></a>Duration:: operator + =

Dodaje liczbę cykli określonego `duration` obiektu do liczby przechowywanych cykli.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Trwania*\
Element `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiekt po dodaniu jest wykonywany.

## <a name="operator-_eq"></a>Duration:: operator-=

Odejmuje liczbę cykli określonego `duration` obiektu od liczby przechowywanych cykli.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Trwania*\
`duration` Obiekt.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiekt po wykonaniu odejmowania.

## <a name="zero"></a>czas trwania:: zero

Zwraca `duration(duration_values<rep>::zero())`wartość.

```cpp
static constexpr duration zero();
```

## <a name="op_mod_eq"></a>Duration:: operator mod =

Zmniejsza liczbę przechowywanych znaczników modulo DIV lub DIV. Count ().

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

*Służąc*\
Dzielnik, który jest obiektem czasu trwania lub wartość reprezentującą liczbę cykli.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zmniejsza liczbę przechowywanych znaczników modulo i zwraca * this. Druga funkcja członkowska zmniejsza liczbę przechowywanych znaczników modulo DIV. Count () i zwraca \*tę wartość.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[duration_values, struktura](../standard-library/duration-values-structure.md)
