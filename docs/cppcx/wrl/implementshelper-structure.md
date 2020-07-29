---
title: ImplementsHelper — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
- implements/Microsoft::WRL::Details::ImplementsHelper::CanCastTo
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
- implements/Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid
- implements/Microsoft::WRL::Details::ImplementsHelper::IidCount
helpviewer_keywords:
- Microsoft::WRL::Details::ImplementsHelper structure
- Microsoft::WRL::Details::ImplementsHelper::CanCastTo method
- Microsoft::WRL::Details::ImplementsHelper::CastToUnknown method
- Microsoft::WRL::Details::ImplementsHelper::FillArrayWithIid method
- Microsoft::WRL::Details::ImplementsHelper::IidCount constant
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
ms.openlocfilehash: d7908670b67df7dbf7b2b74e98f8b59cf30f8e96
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184946"
---
# <a name="implementshelper-structure"></a>ImplementsHelper — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Parametry

*RuntimeClassFlagsT*<br/>
Pole flag określające jeden lub więcej modułów wyliczających [RuntimeClassType —](runtimeclasstype-enumeration.md) .

*ILst*<br/>
Lista identyfikatorów interfejsów.

*IsDelegateToClass*<br/>
Określ **`true`** , czy bieżące wystąpienie programu `Implements` jest klasą bazową pierwszego identyfikatora interfejsu w *ILst*; w przeciwnym razie **`false`** .

## <a name="remarks"></a>Uwagi

Pomaga zaimplementować strukturę [implementującą](implements-structure.md) .

Ten szablon przechodzi przez listę interfejsów i dodaje je jako klasy podstawowe, a także jako informacje niezbędne do włączenia `QueryInterface` .

## <a name="members"></a>Elementy członkowskie

### <a name="protected-methods"></a>Metody chronione

Nazwa                                                    | Opis
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper:: CanCastTo —](#cancastto)               | Pobiera wskaźnik do określonego identyfikatora interfejsu.
[ImplementsHelper:: CastToUnknown —](#casttounknown)       | Pobiera wskaźnik do podstawowego `IUnknown` interfejsu dla bieżącej `Implements` struktury.
[ImplementsHelper:: FillArrayWithIid —](#fillarraywithiid) | Wstawia identyfikator interfejsu określony przez bieżący parametr szablonu zerowego do określonego elementu tablicy.
[ImplementsHelper:: IidCount —](#iidcount)                 | Przechowuje liczbę zaimplementowanych identyfikatorów interfejsów w bieżącym `Implements` obiekcie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ImplementsHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="implementshelpercancastto"></a><a name="cancastto"></a>ImplementsHelper:: CanCastTo —

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);

HRESULT CanCastTo(
   _In_ const IID &iid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Odwołanie do identyfikatora interfejsu.

*ppv*<br/>
Jeśli ta operacja zakończy się pomyślnie, wskaźnik do interfejsu określonego przez *riid* lub *IID*.

*IID*<br/>
Odwołanie do identyfikatora interfejsu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się to powiedzie; w przeciwnym razie wynik HRESULT wskazuje na błąd.

### <a name="remarks"></a>Uwagi

Pobiera wskaźnik do określonego identyfikatora interfejsu.

## <a name="implementshelpercasttounknown"></a><a name="casttounknown"></a>ImplementsHelper:: CastToUnknown —

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do podstawowego `IUnknown` interfejsu.

### <a name="remarks"></a>Uwagi

Pobiera wskaźnik do podstawowego `IUnknown` interfejsu dla bieżącej `Implements` struktury.

## <a name="implementshelperfillarraywithiid"></a><a name="fillarraywithiid"></a>ImplementsHelper:: FillArrayWithIid —

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>Parametry

*indeks*<br/>
Indeks (liczony od zera) wskazujący początkowy element tablicy dla tej operacji. Po zakończeniu tej operacji *indeks* jest zwiększany o 1.

*IID*<br/>
Tablica typu IID.

### <a name="remarks"></a>Uwagi

Wstawia identyfikator interfejsu określony przez bieżący parametr szablonu zerowego do określonego elementu tablicy.

## <a name="implementshelperiidcount"></a><a name="iidcount"></a>ImplementsHelper:: IidCount —

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Uwagi

Przechowuje liczbę zaimplementowanych identyfikatorów interfejsów w bieżącym `Implements` obiekcie.
