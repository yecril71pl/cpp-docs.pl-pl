---
title: combinable — Klasa
ms.date: 11/04/2016
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
ms.openlocfilehash: a1954cd3a69233deed053da5b5fdef0dbc183b80
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141433"
---
# <a name="combinable-class"></a>combinable — Klasa

Obiekt `combinable<T>` jest przeznaczony do dostarczania prywatnych kopii wątku danych w celu wykonania niezależnych od siebie podobliczeń wątku podczas równoległych algorytmów. Na końcu operacji równoległej podobliczenia wątku i prywatnego mogą zostać następnie scalone w wynik końcowy. Ta klasa może być używana zamiast zmiennej udostępnionej i może skutkować zwiększeniem wydajności, jeśli w przeciwnym razie będzie wiele rywalizacji dotyczących tej zmiennej udostępnionej.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
class combinable;
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ danych końcowego scalonego wyniku. Typ musi mieć konstruktora kopiującego i domyślnego konstruktora.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[combinable](#ctor)|Przeciążone. Tworzy nowy obiekt `combinable`.|
|[~ Destruktor z kombinacją](#dtor)|Niszczy obiekt `combinable`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Wyczyść](#clear)|Czyści wszystkie pośrednie wyniki obliczeniowe z poprzedniego użycia.|
|[żądany](#combine)|Oblicza wartość końcową z zestawu podobliczeń wątku lokalnego przez wywołanie dostarczonego Funktor łączenia.|
|[combine_each](#combine_each)|Oblicza wartość końcową z zestawu podobliczeń wątku lokalnego przez wywołanie dostarczonego Funktor, gdy podobliczanie wątku jest podręczne. Końcowy wynik jest kumulowany przez obiekt Function.|
|[local](#local)|Przeciążone. Zwraca odwołanie do podobliczenia wątku-Private.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator =](#operator_eq)|Przypisuje do obiektu `combinable` z innego obiektu `combinable`.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Parallel Containers and Objects](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`combinable`

## <a name="requirements"></a>Wymagania

**Nagłówek:** PPL. h

**Przestrzeń nazw:** współbieżność

## <a name="clear"></a>Wyczyść

Czyści wszystkie pośrednie wyniki obliczeniowe z poprzedniego użycia.

```cpp
void clear();
```

## <a name="ctor"></a>combinable

Tworzy nowy obiekt `combinable`.

```cpp
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu inicjującego Funktor.

*_FnInitialize*<br/>
Funkcja, która zostanie wywołana w celu zainicjowania każdej nowej wartości Private wątku typu `T`. Musi obsługiwać operator wywołania funkcji z podpisem `T ()`.

*_Copy*<br/>
Istniejący obiekt `combinable` do skopiowania do tego obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje nowe elementy z konstruktorem domyślnym dla typu `T`.

Drugi Konstruktor inicjuje nowe elementy przy użyciu Funktor inicjacji dostarczonego jako parametr `_FnInitialize`.

Trzeci konstruktor jest konstruktorem kopiującym.

## <a name="dtor"></a>~ z kombinacją

Niszczy obiekt `combinable`.

```cpp
~combinable();
```

## <a name="combine"></a>żądany

Oblicza wartość końcową z zestawu podobliczeń wątku lokalnego przez wywołanie dostarczonego Funktor łączenia.

```cpp
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany w celu połączenia dwóch podobliczeń wątku lokalnego.

*_FnCombine*<br/>
Funktor, który jest używany do łączenia obliczeń podrzędnych. Jego podpis jest `T (T, T)` lub `T (const T&, const T&)`i musi być asocjacyjny i komutatywna.

### <a name="return-value"></a>Wartość zwrócona

Końcowy wynik łączenia wszystkich podobliczeń wątku-Private.

## <a name="combine_each"></a>combine_each

Oblicza wartość końcową z zestawu podobliczeń wątku lokalnego przez wywołanie dostarczonego Funktor, gdy podobliczanie wątku jest podręczne. Końcowy wynik jest kumulowany przez obiekt Function.

```cpp
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany w celu połączenia pojedynczego podobliczenia wątku lokalnego.

*_FnCombine*<br/>
Funktor, który jest używany do łączenia jednego obliczenia podrzędnego. Jego podpis jest `void (T)` lub `void (const T&)`i musi być asocjacyjny i komutatywna.

## <a name="local"></a>LAN

Zwraca odwołanie do podobliczenia wątku-Private.

```cpp
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>Parametry

*_Exists*<br/>
Odwołanie do wartości logicznej. Wartość logiczna, do której odwołuje się ten argument, zostanie ustawiona na **wartość true** , jeśli podobliczenia, które już istniały w tym wątku, i ustawione na **wartość false** , jeśli było to pierwsze obliczenie podrzędne w tym wątku.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do podobliczenia wątku-Private.

## <a name="operator_eq"></a>operator =

Przypisuje do obiektu `combinable` z innego obiektu `combinable`.

```cpp
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>Parametry

*_Copy*<br/>
Istniejący obiekt `combinable` do skopiowania do tego obiektu.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do tego obiektu `combinable`.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
