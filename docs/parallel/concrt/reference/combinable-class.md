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
ms.openlocfilehash: 05256516c0a693a282b8d0de56d6c9e7465f2740
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299983"
---
# <a name="combinable-class"></a>combinable — Klasa

`combinable<T>` Obiektu mają na celu dostarczenie prywatnego wątku kopie danych w celu wykonywania obliczeń podrzędnych wolne od blokady wątków lokalnych podczas algorytmy równoległe. Na koniec operacji równoległej obliczeń podrzędnych prywatnego wątku może następnie zostać scalony wynik końcowy. Ta klasa można używać zamiast udostępnionej zmiennej i może spowodować zwiększenie wydajności, jeśli w przeciwnym razie będzie wiele rywalizacji o zasoby w tej zmiennej udostępnionych.

## <a name="syntax"></a>Składnia

```
template<typename T>
class combinable;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych scalonych wynik końcowy. Typ musi mieć Konstruktor kopiujący i domyślnego konstruktora.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[combinable —](#ctor)|Przeciążone. Tworzy nowy `combinable` obiektu.|
|[~ combinable — destruktor](#dtor)|Niszczy `combinable` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Usuń zaznaczenie](#clear)|Czyści wszystkie wyniki pośrednie obliczeniową podczas korzystania z poprzedniego.|
|[combine](#combine)|Oblicza wartość końcową z zestawu obliczeń podrzędnych lokalnej wątku, wywołując funkcję łączenia podane.|
|[combine_each](#combine_each)|Oblicza wartość końcową z zestawu obliczeń podrzędnych lokalnej wątku, wywołując funkcję łączenia podane raz na obliczenie podrzędnych lokalnej wątku. Wynik końcowy są zbierane przez obiekt funkcji.|
|[local](#local)|Przeciążone. Zwraca odwołanie do obliczeń podrzędnych prywatnego wątku.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator=](#operator_eq)|Przypisuje `combinable` obiektu z innego `combinable` obiektu.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [równoległe kontenery oraz obiekty](../../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`combinable`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppl.h

**Namespace:** współbieżności

##  <a name="clear"></a> Usuń zaznaczenie

Czyści wszystkie wyniki pośrednie obliczeniową podczas korzystania z poprzedniego.

```
void clear();
```

##  <a name="ctor"></a> combinable —

Tworzy nowy `combinable` obiektu.

```
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funktor inicjowania.

*_FnInitialize*<br/>
Funkcja, która zostanie wywołana w celu zainicjowania każdej nowej wartości prywatnego wątku typu `T`. Sieć VPN musi obsługiwać operatorem wywołania funkcji z podpisem `T ()`.

*_Copy*<br/>
Istniejące `combinable` obiektu do skopiowania do tego.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje nowe elementy przy użyciu domyślnego konstruktora dla typu `T`.

Drugi Konstruktor inicjuje nowe elementy przy użyciu funktor inicjowania podana jako `_FnInitialize` parametru.

Trzeci Konstruktor jest konstruktorem kopiowania.

##  <a name="dtor"></a> ~ combinable —

Niszczy `combinable` obiektu.

```
~combinable();
```

##  <a name="combine"></a> Łączenie

Oblicza wartość końcową z zestawu obliczeń podrzędnych lokalnej wątku, wywołując funkcję łączenia podane.

```
template<typename _Function>
T combine(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, która zostanie wywołana połączyć dwa obliczeń podrzędnych lokalnej wątku.

*_FnCombine*<br/>
Funktorem, który jest używany do łączenia podrzędnego obliczeń. Jego podpis jest `T (T, T)` lub `T (const T&, const T&)`, i musi być asocjacyjna i przemiennego.

### <a name="return-value"></a>Wartość zwracana

Wynik końcowy łączenia wszystkich obliczeń podrzędnych prywatnego wątku.

##  <a name="combine_each"></a> combine_each —

Oblicza wartość końcową z zestawu obliczeń podrzędnych lokalnej wątku, wywołując funkcję łączenia podane raz na obliczenie podrzędnych lokalnej wątku. Wynik końcowy są zbierane przez obiekt funkcji.

```
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, która będzie wywoływana w celu łączenia jednej obliczeń podrzędnych lokalnej wątku.

*_FnCombine*<br/>
Funktorem, który jest używany do łączenia jednej obliczeń podrzędnych. Jego podpis jest `void (T)` lub `void (const T&)`i musi być asocjacyjna i przemiennego.

##  <a name="local"></a> lokalne

Zwraca odwołanie do obliczeń podrzędnych prywatnego wątku.

```
T& local();

T& local(bool& _Exists);
```

### <a name="parameters"></a>Parametry

*_Exists*<br/>
Odwołanie na wartość logiczną. Wartość logiczna, odwołuje się ten argument jest równa **true** Jeśli obliczenie podrzędne już istnieje w tym wątku i ustaw **false** , jakby to była pierwszym obliczeń podrzędnych w tym wątku.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obliczeń podrzędnych prywatnego wątku.

##  <a name="operator_eq"></a> operator =

Przypisuje `combinable` obiektu z innego `combinable` obiektu.

```
combinable& operator= (const combinable& _Copy);
```

### <a name="parameters"></a>Parametry

*_Copy*<br/>
Istniejące `combinable` obiektu do skopiowania do tego.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `combinable` obiektu.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
