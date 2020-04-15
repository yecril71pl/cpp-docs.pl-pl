---
title: SafeInt — Funkcje
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt functions
- SafeAdd
- SafeCast
- SafeDivide
- SafeEquals
- SafeGreaterThan
- SafeGreaterThanEquals
- SafeLessThan
- SafeLessThanEquals
- SafeModulus
- SafeMultiply
- SafeNotEquals
- SafeSubtract
helpviewer_keywords:
- functions, SafeInt
- SafeAdd function
- SafeCast function
- SafeDivide function
- SafeEquals function
- SafeGreaterThan function
- SafeGreaterThanEquals function
- SafeLessThan function
- SafeLessThanEquals function
- SafeModulus function
- SafeMultiply function
- SafeNotEquals function
- SafeSubtract function
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
ms.openlocfilehash: c1c5593aee19254d4348d4e8658ffe9c3f0cf1b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368250"
---
# <a name="safeint-functions"></a>SafeInt — Funkcje

Biblioteka SafeInt udostępnia kilka funkcji, których można używać bez tworzenia wystąpienia [klasy SafeInt.](../safeint/safeint-class.md) Jeśli chcesz chronić pojedynczą operację matematyczną przed przepełnieniem liczby całkowitej, możesz użyć tych funkcji. Jeśli chcesz chronić wiele operacji matematycznych, należy utworzyć `SafeInt` obiekty. Jest bardziej wydajne `SafeInt` do tworzenia obiektów niż do korzystania z tych funkcji wiele razy.

Te funkcje umożliwiają porównywanie lub wykonywanie operacji matematycznych na dwóch różnych typach parametrów bez konieczności konwersji ich na ten sam typ.

Każda z tych funkcji ma `T` `U`dwa typy szablonów: i . Każdy z tych typów może być typu logicznego, znakowego lub integralnego. Typy zintegrowane mogą być podpisane lub niepodpisane i dowolny rozmiar od 8 bitów do 64 bitów.

> [!NOTE]
> Najnowsza wersja tej biblioteki [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)znajduje się pod adresem .

## <a name="in-this-section"></a>W tej sekcji

Funkcja                      | Opis
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | Dodaje dwie liczby i chroni przed przepełnieniem.
[Safecast](#safecast)         | Rzutuje jeden typ parametru na inny typ.
[SafeDivide](#safedivide)     | Dzieli dwie liczby i chroni przed dzieleniem przez zero.
[SafeEquals](#safeequals), [SafeGreaterThan](#safegreaterthan), [SafeGreaterThanEquals](#safegreaterthanequals), [SafeLessThan](#safelessthan), [SafeLessThanEquals](#safelessthanequals), [SafeNotEquals](#safenotequals) | Porównuje dwie liczby. Te funkcje umożliwiają porównywanie dwóch różnych typów liczb bez zmiany ich typów.
[SafeModulus](#safemodulus)   | Wykonuje operację modułu na dwóch liczbach.
[SafeMultiply](#safemultiply) | Mnoży dwie liczby razem i chroni przed przepełnieniem.
[SafeSubtract](#safesubtract) | Odejmuje dwie liczby i chroni przed przepełnieniem.

## <a name="related-sections"></a>Sekcje pokrewne

Sekcja                                                  | Opis
-------------------------------------------------------- | ----------------------------------------------------
[Safeint](../safeint/safeint-class.md)                   | `SafeInt` Klasa.
[SafeIntException (SafeIntException)](../safeint/safeintexception-class.md) | Klasa wyjątku specyficzne dla biblioteki SafeInt.

## <a name="safeadd"></a><a name="safeadd"></a>SafeAdd ( SafeAdd )

Dodaje dwie liczby w sposób, który chroni przed przepełnieniem.

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[w] Pierwszy numer do dodania. Musi to być typ T.

*U*<br/>
[w] Drugi numer do dodania. Musi to być typu U.

*Wynik*<br/>
[na zewnątrz] Parametr, `SafeAdd` w którym przechowuje wynik.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli nie wystąpi żaden błąd; **false,** jeśli wystąpi błąd.

## <a name="safecast"></a><a name="safecast"></a>Safecast

Rzutuje jeden typ liczby na inny typ.

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>Parametry

*Z*<br/>
[w] Numer źródłowy do konwersji. Musi to być `T`typu .

*Do*<br/>
[na zewnątrz] Odwołanie do nowego typu numeru. Musi to być `U`typu .

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli nie wystąpi żaden błąd; **false,** jeśli wystąpi błąd.

## <a name="safedivide"></a><a name="safedivide"></a>SafeDivide (Bezpieczny podział)

Dzieli dwie liczby w sposób chroniący przed dzieleniem przez zero.

```cpp
template<typename T, typename U>
inline bool SafeDivide (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[w] Dzielnik. Musi to być typ T.

*U*<br/>
[w] Dywidenda. Musi to być typu U.

*Wynik*<br/>
[na zewnątrz] Parametr, `SafeDivide` w którym przechowuje wynik.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli nie wystąpi żaden błąd; **false,** jeśli wystąpi błąd.

## <a name="safeequals"></a><a name="safeequals"></a>SafeEquals ( SafeEquals )

Porównuje dwie liczby, aby określić, czy są równe.

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[w] Pierwszy numer do porównania. Musi to być typ T.

*U*<br/>
[w] Druga liczba do porównania. Musi to być typu U.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli *t* i *u* są równe; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Metoda zwiększa, `==` `SafeEquals` ponieważ umożliwia porównanie dwóch różnych typów liczb.

## <a name="safegreaterthan"></a><a name="safegreaterthan"></a>SafeGreaterThan

Porównuje dwie liczby.

```cpp
template<typename T, typename U>
inline bool SafeGreaterThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[w] Pierwszy numer do porównania. Musi to być `T`typu .

*U*<br/>
[w] Druga liczba do porównania. Musi to być `U`typu .

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli *t* jest większa niż *u*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

`SafeGreaterThan`rozszerza operator porównania regularnego, umożliwiając porównanie dwóch różnych typów liczb.

## <a name="safegreaterthanequals"></a><a name="safegreaterthanequals"></a>SafeGreaterThanEquals

Porównuje dwie liczby.

```cpp
template <typename T, typename U>
inline bool SafeGreaterThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[w] Pierwszy numer do porównania. Musi to być `T`typu .

*U*<br/>
[w] Druga liczba do porównania. Musi to być `U`typu .

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli *t* jest większa lub równa *u*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

`SafeGreaterThanEquals`zwiększa standardowy operator porównania, ponieważ umożliwia porównanie dwóch różnych typów liczb.

## <a name="safelessthan"></a><a name="safelessthan"></a>SafeLessDziej

Określa, czy jedna liczba jest mniejsza niż inna.

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[w] Pierwszy numer. Musi to być `T`typu .

*U*<br/>
[w] Drugi numer. Musi to być `U`typu .

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli *t* jest mniejsza niż *u*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta metoda zwiększa standardowy `SafeLessThan` operator porównania, ponieważ umożliwia porównanie dwóch różnych typów liczb.

## <a name="safelessthanequals"></a><a name="safelessthanequals"></a>SafeLessThanequals

Porównuje dwie liczby.

```cpp
template <typename T, typename U>
inline bool SafeLessThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[w] Pierwszy numer do porównania. Musi to być `T`typu .

*U*<br/>
[w] Druga liczba do porównania. Musi to być `U`typu .

### <a name="return-value"></a>Wartość zwracana

**prawda,** jeśli *t* jest mniejsza lub równa *u*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

`SafeLessThanEquals`rozszerza operator porównania regularnego, umożliwiając porównanie dwóch różnych typów liczb.

## <a name="safemodulus"></a><a name="safemodulus"></a>SafeModulus ( SafeModulus )

Wykonuje operację modułu na dwóch liczbach.

```cpp
template<typename T, typename U>
inline bool SafeModulus (
   const T t,
   const U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[w] Dzielnik. Musi to być `T`typu .

*U*<br/>
[w] Dywidenda. Musi to być `U`typu .

*Wynik*<br/>
[na zewnątrz] Parametr, `SafeModulus` w którym przechowuje wynik.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli nie wystąpi żaden błąd; **false,** jeśli wystąpi błąd.

## <a name="safemultiply"></a><a name="safemultiply"></a>SafeMultiply (Bezpiecznemuwciem

Mnoży dwie liczby razem w sposób, który chroni przed przepełnieniem.

```cpp
template<typename T, typename U>
inline bool SafeMultiply (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[w] Pierwsza liczba do pomnożenia. Musi to być `T`typu .

*U*<br/>
[w] Druga liczba do pomnożenia. Musi to być `U`typu .

*Wynik*<br/>
[na zewnątrz] Parametr, `SafeMultiply` w którym przechowuje wynik.

### <a name="return-value"></a>Wartość zwracana

`true`jeśli nie wystąpi żaden błąd; `false` jeśli wystąpi błąd.

## <a name="safenotequals"></a><a name="safenotequals"></a>SafeNotEquals (SafeNotEquals)

Określa, czy dwie liczby nie są równe.

```cpp
template<typename T, typename U>
inline bool SafeNotEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[w] Pierwszy numer do porównania. Musi to być `T`typu .

*U*<br/>
[w] Druga liczba do porównania. Musi to być `U`typu .

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli *t* i *u* nie są równe; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Metoda zwiększa, `!=` `SafeNotEquals` ponieważ umożliwia porównanie dwóch różnych typów liczb.

## <a name="safesubtract"></a><a name="safesubtract"></a>SafeSubtract (SafeSubtract)

Odejmuje dwie liczby w sposób chroniący przed przepełnieniem.

```cpp
template<typename T, typename U>
inline bool SafeSubtract (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[w] Pierwszy numer w odejmowanie. Musi to być `T`typu .

*U*<br/>
[w] Liczba do odjęcie od *t*. Musi to być `U`typu .

*Wynik*<br/>
[na zewnątrz] Parametr, `SafeSubtract` w którym przechowuje wynik.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli nie wystąpi żaden błąd; **false,** jeśli wystąpi błąd.
