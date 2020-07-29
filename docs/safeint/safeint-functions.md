---
title: SafeInt — Funkcje
ms.date: 06/23/2020
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
ms.openlocfilehash: c968601d95403dd63540a7a8ec2190a199fa1c5a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219342"
---
# <a name="safeint-functions"></a>SafeInt — Funkcje

Biblioteka SafeInt zawiera kilka funkcji, których można użyć bez tworzenia wystąpienia [klasy SafeInt](safeint-class.md). Jeśli chcesz chronić pojedynczą operację matematyczną z przepełnienia liczby całkowitej, możesz użyć tych funkcji. Jeśli chcesz chronić wiele operacji matematycznych, należy utworzyć `SafeInt` obiekty. Tworzenie obiektów jest bardziej wydajne `SafeInt` niż używanie tych funkcji wiele razy.

Te funkcje umożliwiają porównywanie lub wykonywanie operacji matematycznych na dwóch różnych typach parametrów bez konieczności konwertowania ich na ten sam typ.

Każda z tych funkcji ma dwa typy szablonów: `T` i `U` . Każdy z tych typów może być wartością logiczną, znakiem lub typem całkowitym. Typy całkowite mogą być podpisane lub niepodpisane oraz mieć dowolny rozmiar z 8 bitów do 64 bitów.

> [!NOTE]
> Najnowsza wersja tej biblioteki znajduje się w lokalizacji [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) .

## <a name="in-this-section"></a>W tej sekcji

Funkcja                      | Opis
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | Dodaje dwie liczby i chroni przed przepełnieniem.
[SafeCast](#safecast)         | Rzutuje jeden typ parametru na inny typ.
[SafeDivide](#safedivide)     | Dzieli dwie liczby i chroni przed podziałem przez zero.
[SafeEquals](#safeequals), [SafeGreaterThan](#safegreaterthan), [SafeGreaterThanEquals](#safegreaterthanequals), [SafeLessThan](#safelessthan), [SafeLessThanEquals](#safelessthanequals), [SafeNotEquals](#safenotequals) | Porównuje dwie liczby. Te funkcje pozwalają porównać dwa różne typy liczb bez zmiany ich typów.
[SafeModulus](#safemodulus)   | Wykonuje operację modułu dla dwóch liczb.
[SafeMultiply](#safemultiply) | Mnoży dwie liczby jednocześnie i chroni przed przepełnieniem.
[SafeSubtract](#safesubtract) | Odejmuje dwie liczby i chroni przed przepełnieniem.

## <a name="related-sections"></a>Sekcje pokrewne

Sekcja                                                  | Opis
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](safeint-class.md)                   | `SafeInt`Klasa.
[SafeIntException](safeintexception-class.md) | Klasa wyjątku określona dla biblioteki SafeInt.

## <a name="safeadd"></a><a name="safeadd"></a>SafeAdd

Dodaje dwie liczby w sposób chroniący przed przepełnieniem.

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*&*<br/>
podczas Pierwsza liczba do dodania. Musi to być typ T.

*'t*<br/>
podczas Druga liczba, która ma zostać dodana. Musi to być typ U.

*wynika*<br/>
określoną Parametr, w którym `SafeAdd` jest przechowywany wynik.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli błąd nie wystąpi; **`false`** Jeśli wystąpi błąd.

## <a name="safecast"></a><a name="safecast"></a>SafeCast

Rzutuje jeden typ liczby na inny typ.

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>Parametry

*Wniosek*<br/>
podczas Numer źródłowy do przekonwertowania. Musi to być typ `T` .

*Do*<br/>
określoną Odwołanie do nowego typu numeru. Musi to być typ `U` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli błąd nie wystąpi; **`false`** Jeśli wystąpi błąd.

## <a name="safedivide"></a><a name="safedivide"></a>SafeDivide

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

*&*<br/>
podczas Dywidenda. Musi to być typ T.

*'t*<br/>
podczas Dzielnik. Musi to być typ U.

*wynika*<br/>
określoną Parametr, w którym `SafeDivide` jest przechowywany wynik.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli błąd nie wystąpi; **`false`** Jeśli wystąpi błąd.

## <a name="safeequals"></a><a name="safeequals"></a>SafeEquals

Porównuje dwie liczby, aby określić, czy są równe.

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*&*<br/>
podczas Pierwsza liczba do porównania. Musi to być typ T.

*'t*<br/>
podczas Druga liczba do porównania. Musi to być typ U.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli *t* i *u* są równe; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Metoda jest ulepszona, `==` ponieważ `SafeEquals` umożliwia porównanie dwóch różnych typów liczb.

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

*&*<br/>
podczas Pierwsza liczba do porównania. Musi to być typ `T` .

*'t*<br/>
podczas Druga liczba do porównania. Musi to być typ `U` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli *t* jest większy niż *u*; w przeciwnym razie **`false`** .

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

*&*<br/>
podczas Pierwsza liczba do porównania. Musi to być typ `T` .

*'t*<br/>
podczas Druga liczba do porównania. Musi to być typ `U` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli *t* jest większy lub równy *u*; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

`SafeGreaterThanEquals`zwiększa standardowy operator porównania, ponieważ umożliwia porównanie dwóch różnych typów liczb.

## <a name="safelessthan"></a><a name="safelessthan"></a>SafeLessThan

Określa, czy jedna liczba jest mniejsza od innej.

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*&*<br/>
podczas Numer pierwszej. Musi to być typ `T` .

*'t*<br/>
podczas Druga liczba. Musi to być typ `U` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli *t* jest mniejsze niż *u*; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Ta metoda podnosi standardowy operator porównania, ponieważ `SafeLessThan` umożliwia porównanie dwóch różnych typów liczby.

## <a name="safelessthanequals"></a><a name="safelessthanequals"></a>SafeLessThanEquals

Porównuje dwie liczby.

```cpp
template <typename T, typename U>
inline bool SafeLessThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*&*<br/>
podczas Pierwsza liczba do porównania. Musi to być typ `T` .

*'t*<br/>
podczas Druga liczba do porównania. Musi to być typ `U` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli *t* jest mniejsze lub równe *u*; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

`SafeLessThanEquals`rozszerza operator porównania regularnego, umożliwiając porównanie dwóch różnych typów liczb.

## <a name="safemodulus"></a><a name="safemodulus"></a>SafeModulus

Wykonuje operację modułu dla dwóch liczb.

```cpp
template<typename T, typename U>
inline bool SafeModulus (
   const T t,
   const U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*&*<br/>
podczas Dzielnik. Musi to być typ `T` .

*'t*<br/>
podczas Dywidenda. Musi to być typ `U` .

*wynika*<br/>
określoną Parametr, w którym `SafeModulus` jest przechowywany wynik.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli błąd nie wystąpi; **`false`** Jeśli wystąpi błąd.

## <a name="safemultiply"></a><a name="safemultiply"></a>SafeMultiply

Mnoży dwie liczby jednocześnie w sposób chroniący przed przepełnieniem.

```cpp
template<typename T, typename U>
inline bool SafeMultiply (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*&*<br/>
podczas Pierwsza liczba do pomnożenia. Musi to być typ `T` .

*'t*<br/>
podczas Druga liczba do pomnożenia. Musi to być typ `U` .

*wynika*<br/>
określoną Parametr, w którym `SafeMultiply` jest przechowywany wynik.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli błąd nie wystąpi; **`false`** Jeśli wystąpi błąd.

## <a name="safenotequals"></a><a name="safenotequals"></a>SafeNotEquals

Określa, czy dwie liczby nie są równe.

```cpp
template<typename T, typename U>
inline bool SafeNotEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parametry

*&*<br/>
podczas Pierwsza liczba do porównania. Musi to być typ `T` .

*'t*<br/>
podczas Druga liczba do porównania. Musi to być typ `U` .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli *t* i *u* nie są równe; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Metoda jest ulepszona, `!=` ponieważ `SafeNotEquals` umożliwia porównanie dwóch różnych typów liczb.

## <a name="safesubtract"></a><a name="safesubtract"></a>SafeSubtract

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

*&*<br/>
podczas Pierwszy numer odejmowania. Musi to być typ `T` .

*'t*<br/>
podczas Liczba, która ma zostać odjęta od *t*. Musi to być typ `U` .

*wynika*<br/>
określoną Parametr, w którym `SafeSubtract` jest przechowywany wynik.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli błąd nie wystąpi; **`false`** Jeśli wystąpi błąd.
