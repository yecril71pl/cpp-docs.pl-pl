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
ms.openlocfilehash: 4a65b7335626cc36a4eecbe61465778889a9e7e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502131"
---
# <a name="modulebase-class"></a>ModuleBase — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
class ModuleBase;
```

## <a name="remarks"></a>Uwagi

Reprezentuje klasę bazową [modułu](../windows/module-class.md) klasy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                         | Opis
-------------------------------------------- | ---------------------------------------------------------
[ModuleBase::ModuleBase](#modulebase)        | Inicjuje wystąpienie `Module` klasy.
[ModuleBase:: ~ ModuleBase](#tilde-modulebase) | Deinicjuje bieżące wystąpienie `Module` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                      | Opis
--------------------------------------------------------- | -------------------------------------------------------------------------
[ModuleBase::DecrementObjectCount](#decrementobjectcount) | Po wdrożeniu, zmniejsza liczbę obiektów śledzone przez moduł.
[ModuleBase::IncrementObjectCount](#incrementobjectcount) | Po wdrożeniu, zwiększa liczbę obiektów śledzonych przez moduł.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ModuleBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="tilde-modulebase"></a>ModuleBase:: ~ ModuleBase

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>Uwagi

Deinicjuje bieżące wystąpienie `ModuleBase` klasy.

## <a name="decrementobjectcount"></a>ModuleBase::DecrementObjectCount

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Liczba przed wykonaniem operacji dekrementacji.

### <a name="remarks"></a>Uwagi

Po wdrożeniu, zmniejsza liczbę obiektów śledzone przez moduł.

## <a name="incrementobjectcount"></a>ModuleBase::IncrementObjectCount

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Liczba przed wykonaniem operacji przyrostu.

### <a name="remarks"></a>Uwagi

Po wdrożeniu, zwiększa liczbę obiektów śledzonych przez moduł.

## <a name="modulebase"></a>ModuleBase::ModuleBase

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
ModuleBase();
```

### <a name="remarks"></a>Uwagi

Inicjuje wystąpienie `Module` klasy.
