---
title: ComPtrRefBase — Klasa
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
- client/Microsoft::WRL::Details::ComPtrRefBase::ptr_
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRefBase class
- Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable** operator
- Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown** operator
- Microsoft::WRL::Details::ComPtrRefBase::ptr_ data member
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
ms.openlocfilehash: 4f6dd6449cf8135ad14486d64cea95d8329e0014
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372617"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>Parametry

*T*<br/>
[ComPtr\<T>](comptr-class.md) typu lub typu pochodnego z niego, a nie tylko interfejs reprezentowany przez . `ComPtr`

## <a name="remarks"></a>Uwagi

Reprezentuje klasę podstawową dla klasy [ComPtrRef.](comptrref-class.md)

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

Nazwa            | Opis
--------------- | -------------------------------------------------
`InterfaceType` | Synonim typu parametru szablonu *T*.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                                                       | Opis
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase::operator IInspectable**](#operator-iinspectable-star-star) | Rzutuje bieżący [element członkowski](#ptr) danych ptr_ do pointer-to-a-pointer-to `IInspectable` interfejsu.
[ComPtrRefBase::operator IUnknown**](#operator-iunknown-star-star)         | Rzutuje bieżący [element członkowski](#ptr) danych ptr_ do pointer-to-a-pointer-to `IUnknown` interfejsu.

### <a name="protected-data-members"></a>Członkowie chronionych danych

Nazwa                        | Opis
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase::ptr_](#ptr) | Wskaźnik do typu określonego przez bieżący parametr szablonu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ComPtrRefBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="comptrrefbaseoperator-iinspectable-operator"></a><a name="operator-iinspectable-star-star"></a>ComPtrRefBase::operator IInspectable\* \* Operator

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>Uwagi

Rzutuje bieżący [element członkowski](#ptr) danych ptr_ do pointer-to-a-pointer-to `IInspectable` interfejsu.

Błąd jest emitowany, jeśli `ComPtrRefBase` prąd nie pochodzi `IInspectable`od .

Ta rzutnia jest `__WRL_CLASSIC_COM__` dostępna tylko wtedy, gdy jest zdefiniowana.

## <a name="comptrrefbaseoperator-iunknown-operator"></a><a name="operator-iunknown-star-star"></a>ComPtrRefBase::operator IUnknown** Operator

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>Uwagi

Rzutuje bieżący [element członkowski](#ptr) danych ptr_ do pointer-to-a-pointer-to `IUnknown` interfejsu.

Błąd jest emitowany, jeśli `ComPtrRefBase` prąd nie pochodzi `IUnknown`od .

## <a name="comptrrefbaseptr_"></a><a name="ptr"></a>ComPtrRefBase::ptr_

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
T* ptr_;
```

### <a name="remarks"></a>Uwagi

Wskaźnik do typu określonego przez bieżący parametr szablonu. `ptr_`jest chronionym elementem członkowskim danych.
