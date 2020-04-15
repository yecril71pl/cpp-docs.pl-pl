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
ms.openlocfilehash: 3669935bf094f476ca24a8170a0388dff29e0a0c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368751"
---
# <a name="duration-class"></a>duration — Klasa

Opisuje typ, który przechowuje *przedział czasu*, który jest czas, który upłynął między dwoma punktami czasu.

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

Argument `Rep` szablonu opisuje typ, który jest używany do przechowywania liczby znaczników zegara w interwale. Argument `Period` szablonu jest wystąpienie [współczynnika,](../standard-library/ratio.md) który opisuje rozmiar interwału, który reprezentuje każdy znacznik.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|czas trwania::period Typedef|Reprezentuje synonim parametru `Period`szablonu .|
|czas trwania::rep Typedef|Reprezentuje synonim parametru `Rep`szablonu .|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Długość](#duration)|Konstruuje `duration` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Liczba](#count)|Zwraca liczbę znaczników zegara w przedziale czasu.|
|[Max](#max)|Statyczny. Zwraca maksymalną dopuszczalną wartość `Ref`parametru szablonu .|
|[Min](#min)|Statyczny. Zwraca najniższą dopuszczalną wartość `Ref`parametru szablonu .|
|[Zero](#zero)|Statyczny. W efekcie `Rep`zwraca (0).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[czas trwania::operator-](#operator-)|Zwraca kopię `duration` obiektu wraz z zanegowanym liczbą znaczników.|
|[czas trwania::operator--](#operator--)|Zmniejsza liczbę przechowywanych znaczników.|
|[czas trwania::operator=](#op_eq)|Zmniejsza liczbę przechowywanych znaczników modulo określoną wartość.|
|[czas trwania::operator*=](#op_star_eq)|Mnoży liczbę przechowywanych znaczników przez określoną wartość.|
|[czas trwania::operator/=](#op_div_eq)|Dzieli liczbę przechowywanych znaczników przez liczbę `duration` znaczników określonego obiektu.|
|[czas trwania::operator+](#op_add)|Zwraca wartość `*this`.|
|[czas trwania::operator++](#op_add_add)|Zwiększa liczbę przechowywanych znaczników.|
|[czas trwania::operator+=](#op_add_eq)|Dodaje liczbę znaczników `duration` określonego obiektu do przechowywanej liczby znaczników.|
|[czas trwania::operator-=](#operator-_eq)|Odejmuje liczbę znaczników `duration` określonego obiektu od przechowywanej liczby znaczników.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono>

**Przestrzeń nazw:** std::chrono

## <a name="durationcount"></a><a name="count"></a>czas trwania::count

Pobiera liczbę znaczników zegara w przedziale czasu.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaczników zegara w przedziale czasu.

## <a name="durationduration-constructor"></a><a name="duration"></a>czas trwania::duration Constructor

Konstruuje `duration` obiekt.

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);

template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>Parametry

*Rep2 (właspr.*\
Typ arytmetyczny reprezentujący liczbę znaczników.

*Okres2*\
Specjalizacja `std::ratio` szablonu reprezentująca okres znacznika w jednostkach sekund.

*R*\
Liczba znaczników okresu domyślnego.

*Dur (Dur)*\
Liczba znaczników okresu określonego przez *Okres2*.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor tworzy obiekt, który jest niezainicjowany. Inicjowanie wartości przy użyciu pustych nawiasów klamrowych inicjuje obiekt, który reprezentuje przedział czasu zero znaczników zegara.

Drugi konstruktor argumentów jednego szablonu konstruuje *R* obiekt reprezentujący interwał czasu `std::ratio<1>`znaczników zegara R przy użyciu domyślnego okresu . Aby uniknąć zaokrąglenia liczby znaczników, jest to błąd do konstruowania obiektu czasu trwania z `duration::rep` reprezentacji typu *Rep2,* które mogą być traktowane jako typu zmiennoprzecinkowego, gdy nie mogą być traktowane jako typu zmiennoprzecinkowego.

Trzeci konstruktor dwóch argumentów szablonu tworzy obiekt reprezentujący przedział czasu, którego długość jest interwałem czasu określonym przez *Dur*. Aby uniknąć obcięcie liczby znaczników, jest to błąd do konstruowania obiektu czasu trwania z innego obiektu czasu trwania, którego typ jest *niewspółmierny* z typem docelowym.

Typ `D1` czasu trwania jest *niewspółmierny* z innym `D2` typem czasu trwania, jeśli `D2` nie można traktować jako typu zmiennoprzecinkowego i ratio_divide [\<D1::period, D2::period>::type::den](../standard-library/ratio.md) nie jest 1.

O ile *Rep2* jest `rep` niejawnie `treat_as_floating_point<rep>`konwertowane i albo *posiada true* lub `treat_as_floating_point<Rep2>`posiada *false,* drugi konstruktor nie uczestniczy w rozpoznawania przeciążenia. Aby uzyskać więcej informacji, zobacz [<type_traits>](../standard-library/type-traits.md).

O ile konwersja nie jest `treat_as_floating_point<rep>`indukowana przepełnienie i `treat_as_floating_point<Rep2>`utrzymuje się na wartości *1*lub oba `ratio_divide<Period2, period>::den` są równe 1 i są *false*, trzeci konstruktor nie uczestniczy w rozpoznawaniu przeciążenia. Aby uzyskać więcej informacji, zobacz [<type_traits>](../standard-library/type-traits.md).

## <a name="durationmax"></a><a name="max"></a>czas trwania::maks.

Metoda statyczna, która zwraca górną granicę dla wartości typu `Ref`parametru szablonu .

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie `duration(duration_values<rep>::max())`zwraca .

## <a name="durationmin"></a><a name="min"></a>czas trwania::min

Metoda statyczna, która zwraca dolną granicę dla wartości typu `Ref`parametru szablonu .

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie `duration(duration_values<rep>::min())`zwraca .

## <a name="durationoperator-"></a><a name="operator-"></a>czas trwania::operator-

Zwraca kopię `duration` obiektu wraz z zanegowanym liczbą znaczników.

```cpp
constexpr duration operator-() const;
```

## <a name="durationoperator--"></a><a name="operator--"></a>czas trwania::operator--

Zmniejsza liczbę przechowywanych znaczników.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza metoda `*this`zwraca .

Druga metoda zwraca kopię `*this` tego jest przed dekrementacji.

## <a name="durationoperator"></a><a name="op_eq"></a>czas trwania::operator=

Zmniejsza liczbę przechowywanych znaczników modulo określoną wartość.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

*Div*\
Dla pierwszej metody *Div* reprezentuje liczbę znaczników. Dla drugiej metody *Div* `duration` jest obiektem, który zawiera liczbę znaczników.

### <a name="return-value"></a>Wartość zwracana

Obiekt `duration` po wykonaniu operacji modulo.

## <a name="durationoperator"></a><a name="op_star_eq"></a>czas trwania::operator*=

Mnoży liczbę przechowywanych znaczników przez określoną wartość.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Parametry

*Mult*\
Wartość typu określonego przez `duration::rep`.

### <a name="return-value"></a>Wartość zwracana

Obiekt `duration` po wykonaniu mnożenia.

## <a name="durationoperator"></a><a name="op_div_eq"></a>czas trwania::operator/=

Dzieli liczbę przechowywanych znaczników przez określoną wartość.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Parametry

*Div*\
Wartość typu określonego przez `duration::rep`.

### <a name="return-value"></a>Wartość zwracana

Obiekt `duration` po wykonaniu podziału.

## <a name="durationoperator"></a><a name="op_add"></a>czas trwania::operator+

Zwraca wartość `*this`.

```cpp
constexpr duration operator+() const;
```

## <a name="durationoperator"></a><a name="op_add_add"></a>czas trwania::operator++

Zwiększa liczbę przechowywanych znaczników.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza metoda `*this`zwraca .

Druga metoda zwraca kopię `*this` tego jest dokonywana przed przyrostem.

## <a name="durationoperator"></a><a name="op_add_eq"></a>czas trwania::operator+=

Dodaje liczbę znaczników `duration` określonego obiektu do przechowywanej liczby znaczników.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Dur (Dur)*\
Obiekt `duration`.

### <a name="return-value"></a>Wartość zwracana

Obiekt `duration` po dodaniu jest wykonywany.

## <a name="durationoperator-"></a><a name="operator-_eq"></a>czas trwania::operator-=

Odejmuje liczbę znaczników `duration` określonego obiektu od przechowywanej liczby znaczników.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Dur (Dur)*\
Obiekt `duration`.

### <a name="return-value"></a>Wartość zwracana

Obiekt `duration` po wykonaniu odejmowania.

## <a name="durationzero"></a><a name="zero"></a>czas trwania::zero

Zwraca wartość `duration(duration_values<rep>::zero())`.

```cpp
static constexpr duration zero();
```

## <a name="durationoperator-mod"></a><a name="op_mod_eq"></a>czas trwania::operator mod=

Zmniejsza liczbę przechowywanych znaczników modulo Div lub Div.count().

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

*Div*\
Dzielnik, który jest obiektem czasu trwania lub wartością reprezentującą liczbę znaczników.

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu członkowskiego zmniejsza liczbę przechowywanych znaczników modulo Div i zwraca *this. Funkcja drugiego elementu członkowskiego zmniejsza liczbę przechowywanych znaczników modulo div.count() i zwraca \*tę wartość.

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<>chrono](../standard-library/chrono.md)\
[duration_values — Struktura](../standard-library/duration-values-structure.md)
