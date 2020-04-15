---
title: RuntimeClassBaseT — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::AsIID
- implements/Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS
helpviewer_keywords:
- Microsoft::WRL::Details::RuntimeClassBaseT structure
- Microsoft::WRL::Details::RuntimeClassBaseT::AsIID method
- Microsoft::WRL::Details::RuntimeClassBaseT::GetImplementedIIDS method
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
ms.openlocfilehash: 06a9f73e00d541b0e5bcbe20c57befe4a67c5132
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375722"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
template <unsigned int RuntimeClassTypeT>
friend struct Details::RuntimeClassBaseT;
```

### <a name="parameters"></a>Parametry

*Typ klasy środowiska uruchomieniowego*<br/>
Pole flag określające co najmniej jeden wyliczaratorów [RuntimeClassType.](runtimeclasstype-enumeration.md)

## <a name="remarks"></a>Uwagi

Udostępnia metody pomocnicze dla `QueryInterface` operacji i uzyskiwania identyfikatorów interfejsu.

## <a name="members"></a>Elementy członkowskie

### <a name="protected-methods"></a>Metody chronione

Nazwa                                                         | Opis
------------------------------------------------------------ | -----------------------------------------------------------------------------
[RuntimeClassBaseT::AsiID](#asiid)                           | Pobiera wskaźnik do określonego identyfikatora interfejsu.
[RuntimeClassBaseT::GetImplementediIDS](#getimplementediids) | Pobiera tablicę identyfikatorów interfejsu, które są implementowane przez określony typ.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`RuntimeClassBaseT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="runtimeclassbasetasiid"></a><a name="asiid"></a>RuntimeClassBaseT::AsiID

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

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
Typ, który implementuje identyfikator interfejsu określony przez parametr *riid*.

*Implementuje*<br/>
Zmienna typu określonego przez parametr szablonu *T*.

*Riid*<br/>
Identyfikator interfejsu do pobrania.

*ppvObiekt*<br/>
Jeśli ta operacja zakończy się pomyślnie, wskaźnik do wskaźnika do interfejsu określonego przez parametr *riid*.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie hresult, który opisuje błąd.

### <a name="remarks"></a>Uwagi

Pobiera wskaźnik do określonego identyfikatora interfejsu.

## <a name="runtimeclassbasetgetimplementediids"></a><a name="getimplementediids"></a>RuntimeClassBaseT::GetImplementediIDS

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

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
Typ parametru *implements.*

*Implementuje*<br/>
Wskaźnik do typu określonego przez parametr *T*.

*iidCount (licz) iidCount*<br/>
Maksymalna liczba identyfikatorów interfejsu do pobrania.

*iids*<br/>
Jeśli ta operacja zakończy się pomyślnie, tablica identyfikatorów interfejsu zaimplementowana przez typ *T*.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie hresult, który opisuje błąd.

### <a name="remarks"></a>Uwagi

Pobiera tablicę identyfikatorów interfejsu, które są implementowane przez określony typ.
