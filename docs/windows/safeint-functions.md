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
ms.openlocfilehash: 0cf1418e3bf00c037faaa67de2bc76ad2b7cc5e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578402"
---
# <a name="safeint-functions"></a>SafeInt — Funkcje

Biblioteka SafeInt udostępnia kilka funkcji, których można używać bez tworzenia wystąpienia obiektu [safeint — klasa](../windows/safeint-class.md). Jeśli chcesz chronić jednej operacji matematycznych przepełnienie liczby całkowitej, można użyć tych funkcji. Jeśli chcesz chronić wiele operacji matematycznych, należy utworzyć `SafeInt` obiektów. Jest bardziej wydajne, aby utworzyć `SafeInt` obiektów, niż można użyć tych funkcji wiele razy.

Te funkcje umożliwiają porównywania albo do wykonywania operacji matematycznych na dwa różne typy parametrów bez konieczności konwertowania ich najpierw do tego samego typu.

Każda z tych funkcji są dostępne dwa typy szablonów: `T` i `U`. Każdy z tych typów może być atrybut typu wartość logiczna, znak lub typu całkowitego. Typy całkowite mogą być podpisane lub niepodpisane i dowolnego rozmiaru, od 8 bitów na 64-bitowy.

> [!NOTE]
> Najnowszą wersję tej biblioteki znajduje się w [ https://github.com/dcleblanc/SafeInt ](https://github.com/dcleblanc/SafeInt).

## <a name="in-this-section"></a>W tej sekcji

Funkcja                      | Opis
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | Dodaje dwie liczby i chroni przed przepełnienia.
[SafeCast](#safecast)         | Rzutuje jeden typ parametru do innego typu.
[SafeDivide](#safedivide)     | Dzieli dwie liczby i chroni przed dzielenie przez zero.
[SafeEquals](#safeequals), [SafeGreaterThan](#safegreaterthan), [SafeGreaterThanEquals](#safegreaterthanequals), [SafeLessThan](#safelessthan), [SafeLessThanEquals](#safelessthanequals), [ SafeNotEquals](#safenotequals) | Porównuje dwie liczby. Te funkcje pozwalają porównać dwa różne typy liczb bez zmiany ich typy.
[SafeModulus](#safemodulus)   | Wykonuje operację modulo na dwóch liczb.
[SafeMultiply](#safemultiply) | Mnoży dwie liczby ze sobą i chroni przed przepełnienia.
[SafeSubtract](#safesubtract) | Odejmuje dwie liczby i chroni przed przepełnienia.

## <a name="related-sections"></a>Sekcje pokrewne

Sekcja                                                  | Opis
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](../windows/safeint-class.md)                   | `SafeInt` Klasy.
[Safeintexception —](../windows/safeintexception-class.md) | Biblioteka SafeInt specyficzne klasy wyjątku.

## <a name="safeadd"></a>SafeAdd

Dodaje dwie liczby, w sposób zapewniający ochronę przed przepełnienia.

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
[in] Pierwsza liczba do dodania. To musi być typu T.

*u*<br/>
[in] Druga liczba do dodania. Musi mieć typ U.

*wynik*<br/>
[out] Parametr gdzie `SafeAdd` zapisuje wynik.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli żaden błąd nie wystąpi; **false** w przypadku wystąpienia błędu.

## <a name="safecast"></a>SafeCast

Rzutuje jednym typie liczby do innego typu.

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>Parametry

*From*<br/>
[in] Liczba źródłowych, która ma zostać przekształcona. To musi być typu `T`.

*To*<br/>
[out] Odwołanie do nowego typu Liczba. To musi być typu `U`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli żaden błąd nie wystąpi; **false** w przypadku wystąpienia błędu.

## <a name="safedivide"></a>SafeDivide

Dzieli dwie liczby, w sposób zapewniający ochronę przed dzielenie przez zero.

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
[in] Dzielnik. To musi być typu T.

*u*<br/>
[in] Dzielna. Musi mieć typ U.

*wynik*<br/>
[out] Parametr gdzie `SafeDivide` zapisuje wynik.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli żaden błąd nie wystąpi; **false** w przypadku wystąpienia błędu.

## <a name="safeequals"></a>SafeEquals

Porównuje dwie liczby, aby ustalić, czy są równe.

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] Pierwsza liczba do porównania. To musi być typu T.

*u*<br/>
[in] Druga liczba do porównania. Musi mieć typ U.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *t* i *u* są równe; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Rozszerza metoda `==` ponieważ `SafeEquals` umożliwia porównywanie dwa różne typy liczb.

## <a name="safegreaterthan"></a>SafeGreaterThan

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
[in] Pierwsza liczba do porównania. To musi być typu `T`.

*u*<br/>
[in] Druga liczba do porównania. To musi być typu `U`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *t* jest większa niż *u*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

`SafeGreaterThan` Rozszerza operator porównania regularnych, dzięki któremu można porównać dwa różne typy liczb.

## <a name="safegreaterthanequals"></a>SafeGreaterThanEquals

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
[in] Pierwsza liczba do porównania. To musi być typu `T`.

*u*<br/>
[in] Druga liczba do porównania. To musi być typu `U`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *t* jest większa niż lub równa *u*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

`SafeGreaterThanEquals` zwiększa operator porównania standardowe, ponieważ umożliwia porównywanie dwa różne typy liczb.

## <a name="safelessthan"></a>SafeLessThan

Określa, czy jeden jest mniejszy niż inny.

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] Pierwsza liczba. To musi być typu `T`.

*u*<br/>
[in] Drugi numer. To musi być typu `U`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *t* jest mniejsza niż *u*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Ta metoda zwiększa operator porównania standardowe, ponieważ `SafeLessThan` umożliwia porównywanie dwa różne typy liczby.

## <a name="safelessthanequals"></a>SafeLessThanEquals

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
[in] Pierwsza liczba do porównania. To musi być typu `T`.

*u*<br/>
[in] Druga liczba do porównania. To musi być typu `U`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *t* jest mniejsza niż lub równa *u*; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

`SafeLessThanEquals` Rozszerza operator porównania regularnych, dzięki któremu można porównać dwa różne typy liczb.

## <a name="safemodulus"></a>SafeModulus

Wykonuje operację modulo na dwóch liczb.

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
[in] Dzielnik. To musi być typu `T`.

*u*<br/>
[in] Dzielna. To musi być typu `U`.

*wynik*<br/>
[out] Parametr gdzie `SafeModulus` zapisuje wynik.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli żaden błąd nie wystąpi; **false** w przypadku wystąpienia błędu.

## <a name="safemultiply"></a>SafeMultiply

Mnoży dwie liczby razem w sposób zapewniający ochronę przed przepełnienia.

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
[in] Pierwszy numer do pomnożenia. To musi być typu `T`.

*u*<br/>
[in] Druga liczba do pomnożenia. To musi być typu `U`.

*wynik*<br/>
[out] Parametr gdzie `SafeMultiply` zapisuje wynik.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli żaden błąd nie wystąpi; `false` w przypadku wystąpienia błędu.

## <a name="safenotequals"></a>SafeNotEquals

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
[in] Pierwsza liczba do porównania. To musi być typu `T`.

*u*<br/>
[in] Druga liczba do porównania. To musi być typu `U`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *t* i *u* nie są równe; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Rozszerza metoda `!=` ponieważ `SafeNotEquals` umożliwia porównywanie dwa różne typy liczb.

## <a name="safesubtract"></a>SafeSubtract

Odejmuje dwie liczby, w sposób zapewniający ochronę przed przepełnienia.

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
[in] Pierwszy numer w odejmowania. To musi być typu `T`.

*u*<br/>
[in] Liczba, którą chcesz odjąć od *t*. To musi być typu `U`.

*wynik*<br/>
[out] Parametr gdzie `SafeSubtract` zapisuje wynik.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli żaden błąd nie wystąpi; **false** w przypadku wystąpienia błędu.
