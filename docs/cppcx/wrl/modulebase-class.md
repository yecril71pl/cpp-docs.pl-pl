---
title: ModuleBase — Klasa
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::~ModuleBase
helpviewer_keywords:
- ModuleBase class
- Microsoft::WRL::Details::ModuleBase::DecrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::IncrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::ModuleBase, constructor
- Microsoft::WRL::Details::ModuleBase::~ModuleBase, destructor
ms.assetid: edce7591-6893-46f7-94a7-382827775548
ms.openlocfilehash: 13a8ceef3133e9946524e1fcd02e96535eccd7fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371259"
---
# <a name="modulebase-class"></a>ModuleBase — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
class ModuleBase;
```

## <a name="remarks"></a>Uwagi

Reprezentuje klasę podstawową [module](module-class.md) klas.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                         | Opis
-------------------------------------------- | ---------------------------------------------------------
[Baza modułów::Baza modułów](#modulebase)        | Inicjuje wystąpienie klasy `Module`.
[Baza modułów::~Baza modułów](#tilde-modulebase) | Deinitializes bieżące wystąpienie `Module` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                      | Opis
--------------------------------------------------------- | -------------------------------------------------------------------------
[Baza modułów::DekrówoblicznikObjectCount](#decrementobjectcount) | Po zaimplementowaniu zmniejsza liczbę obiektów śledzonych przez moduł.
[Baza modułów::IncrementObjectCount](#incrementobjectcount) | Po zaimplementowaniu zwiększa liczbę obiektów śledzonych przez moduł.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ModuleBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="modulebasemodulebase"></a><a name="tilde-modulebase"></a>Baza modułów::~Baza modułów

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>Uwagi

Deinitializes bieżące wystąpienie `ModuleBase` klasy.

## <a name="modulebasedecrementobjectcount"></a><a name="decrementobjectcount"></a>Baza modułów::DekrówoblicznikObjectCount

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Liczba przed operacją dekrementacji.

### <a name="remarks"></a>Uwagi

Po zaimplementowaniu zmniejsza liczbę obiektów śledzonych przez moduł.

## <a name="modulebaseincrementobjectcount"></a><a name="incrementobjectcount"></a>Baza modułów::IncrementObjectCount

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Liczba przed operacją przyrostu.

### <a name="remarks"></a>Uwagi

Po zaimplementowaniu zwiększa liczbę obiektów śledzonych przez moduł.

## <a name="modulebasemodulebase"></a><a name="modulebase"></a>Baza modułów::Baza modułów

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
ModuleBase();
```

### <a name="remarks"></a>Uwagi

Inicjuje wystąpienie klasy `Module`.
