---
title: RuntimeClassBaseT, struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c9e7f5b38d3434e8753646db4733218978e7e766
ms.sourcegitcommit: edb46b0239a0e616af4ec58906e12338c3e8d2c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47169713"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <
   unsigned int RuntimeClassTypeT
>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>Parametry

*RuntimeClassTypeT*<br/>
Pola flagi, które określa co najmniej jeden [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) modułów wyliczających.

## <a name="remarks"></a>Uwagi

Zapewnia metody pomocnika do `QueryInterface` operacji oraz pobieranie identyfikatorów interfejsu.

## <a name="members"></a>Elementy członkowskie

### <a name="protected-methods"></a>Metody chronione

Nazwa                                                         | Opis
------------------------------------------------------------ | -----------------------------------------------------------------------------
[RuntimeClassBaseT::AsIID](#asiid)                           | Pobiera wskaźnik do określonego interfejsu.
[RuntimeClassBaseT::GetImplementedIIDS](#getimplementediids) | Pobiera tablicę identyfikatorów, które są implementowane przez określony typ interfejsu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`RuntimeClassBaseT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="asiid"></a>RuntimeClassBaseT::AsIID

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
template<typename T>
__forceinline static HRESULT AsIID(
   _In_ T* implements,
   REFIID riid,
   _Deref_out_ void **ppvObject
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ, który implementuje Identyfikatorem określony przez parametr *riid*.

*Implementuje*<br/>
Zmiennej o typie określonym przez parametr szablonu *T*.

*Parametr riid*<br/>
Identyfikator interfejsu do pobrania.

*ppvObject*<br/>
Jeśli operacja się powiedzie, wskaźnik do a wskaźnik do interfejsu określony przez parametr *riid*.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.

### <a name="remarks"></a>Uwagi

Pobiera wskaźnik do określonego interfejsu.

## <a name="getimplementediids"></a>RuntimeClassBaseT::GetImplementedIIDS

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
template<typename T>
__forceinline static HRESULT GetImplementedIIDS(
   _In_ T* implements,
   _Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ *implementuje* parametru.

*Implementuje*<br/>
Wskaźnik do typu określonego przez parametr *T*.

*iidCount*<br/>
Maksymalna liczba identyfikatorów interfejsu do pobrania.

*IID*<br/>
Jeśli operacja zakończy się pomyślnie, tablicę identyfikatorów implementowana przez typ interfejsu *T*.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd.

### <a name="remarks"></a>Uwagi

Pobiera tablicę identyfikatorów, które są implementowane przez określony typ interfejsu.
