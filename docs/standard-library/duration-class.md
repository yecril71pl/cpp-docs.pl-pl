---
title: czas trwania klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
dev_langs:
- C++
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::chrono [C++], duration
ms.workload:
- cplusplus
ms.openlocfilehash: fe02890ce8d8dcde099f4b91b23c770b2e36c96d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33847949"
---
# <a name="duration-class"></a>duration — Klasa

Opisuje typ, który przechowuje *interwał czasu*, która jest czas, który upłynął między dwoma punktami czasu.

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

Argument szablonu `Rep` opisuje typ, który służy do przechowywania liczbę taktów zegara w interwale. Argument szablonu `Period` jest instancją typu [współczynnik](../standard-library/ratio.md) opisujący rozmiar interwału reprezentujący poszczególnych znaczników.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Definicje typów publicznych

|Nazwa|Opis|
|----------|-----------------|
|DURATION::Period — Typedef|Reprezentuje synonim parametru szablonu `Period`.|
|DURATION::Rep — Typedef|Reprezentuje synonim parametru szablonu `Rep`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Czas trwania](#duration)|Konstruuje `duration` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Liczba](#count)|Zwraca liczbę zegarowych w interwale czasu.|
|[max](#max)|Statyczna. Zwraca maksymalna dozwolona wartość parametru szablonu `Ref`.|
|[min](#min)|Statyczna. Zwraca Najmniejsza dozwolona wartość parametru szablonu `Ref`.|
|[zero](#zero)|Statyczna. W efekcie zwraca `Rep`(0).|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[DURATION::operator-](#operator-)|Zwraca kopię `duration` obiektu wraz z liczbą zanegowaną znaczników.|
|[DURATION::operator--](#operator--)|Zmniejsza liczba przechowywanych znaczników.|
|[DURATION::operator =](#op_eq)|Zmniejsza liczbę przechowywanych znaczników modulo określoną wartość.|
|[DURATION::operator * =](#op_star_eq)|Mnoży liczbę cykli przechowywanych przez określoną wartość.|
|[DURATION::operator / =](#op_div_eq)|Dzieli liczbę cykli przechowywanych przez liczbę cykli określonej `duration` obiektu.|
|[DURATION::operator +](#op_add)|Zwraca `*this`.|
|[DURATION::operator ++](#op_add_add)|Zwiększa liczbę przechowywanych znaczników.|
|[DURATION::operator +=](#op_add_eq)|Dodaje liczbę cykli określonej `duration` obiekt, aby liczba cykli przechowywane.|
|[DURATION::operator-=](#operator-_eq)|Odejmuje liczbę cykli określonej `duration` obiektu liczba cykli przechowywane.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono >

**Namespace:** std::chrono

## <a name="count"></a>  DURATION::Count

Pobiera liczbę taktów zegara w interwale czasu.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba zegarowych w interwale czasu.

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

`Rep2` Typ arytmetyczny, aby reprezentować liczbę znaczników.

`Period2` A `std::ratio` specjalizacja szablonu do reprezentowania okres znaczników w jednostkach czasu w sekundach.

`R` Liczba Takty domyślnego okresu.

`Dur` Liczba znaczników czasu określonego przez `Period2`.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor konstrukcji obiektu, który nie został zainicjowany. Inicjowanie wartości przy użyciu pustymi nawiasami klamrowymi inicjuje obiekt, który reprezentuje interwały czasu zeru cykli zegara.

Drugi, jeden szablon argumentów konstruktora tworzy obiekt reprezentujący interwał czasu `R` przy użyciu domyślnego okresu Takty zegara `std::ratio<1>`. Aby uniknąć zaokrąglenia liczby cykli, występuje błąd do utworzenia obiektu czasu trwania z typem reprezentacja `Rep2` może być traktowana jako zmiennoprzecinkowe wpisz kiedy `duration::rep` nie może być traktowana jako typ zmiennoprzecinkowy.

Trzeci, dwa konstruktora argumentów szablonu tworzy obiekt, który reprezentuje przedział czasu, w której długość jest przedział czasu, który jest określony przez `Dur`. Aby uniknąć obcięcie liczby cykli, występuje błąd do utworzenia obiektu czasu trwania z innego obiektu czas trwania, którego typ jest *incommensurable* z typem docelowym.

Wpisz czas trwania `D1` jest *incommensurable* z innym typem czas trwania `D2` Jeśli `D2` nie może być traktowana jako typ zmiennoprzecinkowy i [ratio_divide\<D1::period, D2:: okres >:: type::den](../standard-library/ratio.md) nie jest 1.

O ile `Rep2` niejawnie przekonwertować `rep` i `treat_as_floating_point<rep>` *jest spełniony* lub `treat_as_floating_point<Rep2>` *przechowuje false*, drugi Konstruktor nie uczestniczy w Rozpoznanie przeciążenia. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

O ile nie przepełnienie wywołana podczas konwersji i `treat_as_floating_point<rep>` *jest spełniony*, lub obie `ratio_divide<Period2, period>::den` jest równa 1 i `treat_as_floating_point<Rep2>` *ma wartość false*, trzeci Konstruktor nie uczestniczy w Rozpoznanie przeciążenia. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

## <a name="max"></a>  DURATION::Max

Statyczną metodę, która zwraca górną granicę dla wartości typu parametru szablonu `Ref`.

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca `duration(duration_values<rep>::max())`.

## <a name="min"></a>  DURATION::min

Statyczną metodę, która zwraca dolną granicę dla wartości typu parametru szablonu `Ref`.

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca `duration(duration_values<rep>::min())`.

## <a name="duration__operator-"></a>  DURATION::operator-

Zwraca kopię `duration` obiektu wraz z liczbą zanegowaną znaczników.

```cpp
constexpr duration operator-() const;
```

## <a name="duration__operator--"></a>  DURATION::operator--

Zmniejsza liczba przechowywanych znaczników.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza metoda zwraca `*this`.

Druga metoda zwraca kopię `*this` który staje się przed zmniejszenie.

## <a name="op_eq"></a>  DURATION::operator =

Zmniejsza liczbę przechowywanych znaczników modulo określoną wartość.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

`Div` W przypadku pierwszej metody `Div` reprezentuje liczbę cykli. W przypadku drugiego metody `Div` jest `duration` obiekt, który zawiera liczbę cykli.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiektu po modulo operacja jest wykonywana.

## <a name="op_star_eq"></a>  DURATION::operator * =

Mnoży liczbę cykli przechowywanych przez określoną wartość.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Parametry

`Mult` Wartość typu, który jest określony przez `duration::rep`.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiektu po wykonaniu mnożenia.

## <a name="op_div_eq"></a>  DURATION::operator / =

Dzieli liczbę cykli przechowywanych przez określoną wartość.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Parametry

`Div` Wartość typu, który jest określony przez `duration::rep`.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiekt dzielenia.

## <a name="op_add"></a>  DURATION::operator +

Zwraca `*this`.

```cpp
constexpr duration operator+() const;
```

## <a name="op_add_add"></a>  DURATION::operator ++

Zwiększa liczbę przechowywanych znaczników.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza metoda zwraca `*this`.

Druga metoda zwraca kopię `*this` który staje się przed przyrostu.

## <a name="op_add_eq"></a>  DURATION::operator +=

Dodaje liczbę cykli określonej `duration` obiekt, aby liczba cykli przechowywane.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

`Dur` A `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiektu po wykonaniu operacji dodawania.

## <a name="duration__operator-_eq"></a>  DURATION::operator-=

Odejmuje liczbę cykli określonej `duration` obiektu liczba cykli przechowywane.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

`Dur` A `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

`duration` Obiektu po wykonaniu odejmowania.

## <a name="zero"></a>  DURATION::zero

Zwraca `duration(duration_values<rep>::zero())`.

```cpp
static constexpr duration zero();
```

## <a name="op_mod_eq"></a>  DURATION::operator mod =

Zmniejsza liczbę przechowywanych znaczników modulo Div lub Div.count().

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parametry

`Div` Zlicza dzielnik, który jest obiektem czasu trwania lub wartość, która reprezentuje znaczników.

### <a name="remarks"></a>Uwagi

Pierwszy funkcji członkowskiej zmniejsza liczbę przechowywanych znaczników modulo Div i zwraca * to. Drugi funkcji członkowskiej zmniejsza liczbę przechowywanych znaczników modulo Div.count() i zwraca \*to.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[duration_values, struktura](../standard-library/duration-values-structure.md)<br/>
