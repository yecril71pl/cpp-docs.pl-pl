---
title: Comptrrefbase — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
- client/Microsoft::WRL::Details::ComPtrRefBase::ptr_
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRefBase class
- Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable** operator
- Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown** operator
- Microsoft::WRL::Details::ComPtrRefBase::ptr_ data member
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 79b7c3df2b6d3dc338ecda713b4ec406c8964cab
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789257"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>Parametry

*T*<br/>
A [ComPtr\<T >](../windows/comptr-class.md) typu lub typu pochodnego w nie tylko interfejs, reprezentowane przez `ComPtr`.

## <a name="remarks"></a>Uwagi

Reprezentuje klasę bazową dla [comptrref —](../windows/comptrref-class.md) klasy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa            | Opis
--------------- | -------------------------------------------------
`InterfaceType` | Synonim dla typu parametru szablonu *T*.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                                                       | Opis
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase::operator IInspectable **](#operator-iinspectable-star-star) | Rzutuje bieżącego [ptr_ — element](#ptr) element członkowski danych do wskaźnik do a wskaźnik do `IInspectable` interfejsu.
[ComPtrRefBase::operator IUnknown **](#operator-iunknown-star-star)         | Rzutuje bieżącego [ptr_ — element](#ptr) element członkowski danych do wskaźnik do a wskaźnik do `IUnknown` interfejsu.

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

Nazwa                        | Opis
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase::ptr_](#ptr) | Wskaźnik do typu określonego przez parametr bieżącego szablonu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ComPtrRefBase`

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::wrl:: details

## <a name="operator-iinspectable-star-star"></a>ComPtrRefBase::operator IInspectable\* \* — Operator

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>Uwagi

Rzutuje bieżącego [ptr_ — element](#ptr) element członkowski danych do wskaźnik do a wskaźnik do `IInspectable` interfejsu.

Błąd jest emitowane, jeśli bieżący `ComPtrRefBase` nie pochodzi od `IInspectable`.

To rzutowanie jest dostępna tylko wtedy, gdy `__WRL_CLASSIC_COM__` jest zdefiniowana.

## <a name="operator-iunknown-star-star"></a>Operator ComPtrRefBase::operator IUnknown **

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>Uwagi

Rzutuje bieżącego [ptr_ — element](#ptr) element członkowski danych do wskaźnik do a wskaźnik do `IUnknown` interfejsu.

Błąd jest emitowane, jeśli bieżący `ComPtrRefBase` nie pochodzi od `IUnknown`.

## <a name="ptr"></a>ComPtrRefBase::ptr_

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
T* ptr_;
```

### <a name="remarks"></a>Uwagi

Wskaźnik do typu określonego przez parametr bieżącego szablonu. `ptr_` jest członkiem chronionych danych.
