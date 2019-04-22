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
ms.openlocfilehash: 250a59152e9b41eb48c453caaa696fdc8ca3d3b4
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787495"
---
# <a name="implementshelper-structure"></a>ImplementsHelper — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Parametry

*RuntimeClassFlagsT*<br/>
Pola flagi, które określa co najmniej jeden [RuntimeClassType](runtimeclasstype-enumeration.md) modułów wyliczających.

*IList*<br/>
Lista identyfikatorów interfejsu.

*IsDelegateToClass*<br/>
Określ **true** Jeśli bieżące wystąpienie `Implements` będąca klasą bazową identyfikator pierwszego interfejsu w *IList*; w przeciwnym razie **false**.

## <a name="remarks"></a>Uwagi

Pomaga wdrożyć [implementuje](implements-structure.md) struktury.

Ten szablon przechodzi przez listę interfejsów i dodaje je w klasach bazowych, jak i informacje niezbędne do umożliwienia `QueryInterface`.

## <a name="members"></a>Elementy członkowskie

### <a name="protected-methods"></a>Metody chronione

Nazwa                                                    | Opis
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper::CanCastTo](#cancastto)               | Pobiera wskaźnik do określonego interfejsu.
[ImplementsHelper::CastToUnknown](#casttounknown)       | Pobiera wskaźnik do bazowego `IUnknown` interfejsu dla bieżącego `Implements` struktury.
[ImplementsHelper::FillArrayWithIid](#fillarraywithiid) | Wstawia identyfikator interfejsu określonego przez bieżący parametr szablonu zerowego do elementu określonej tablicy.
[ImplementsHelper::IidCount](#iidcount)                 | Przechowuje liczbę zaimplementowanego interfejsu identyfikatorów w bieżącym `Implements` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ImplementsHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="cancastto"></a>ImplementsHelper::CanCastTo

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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

*Parametr riid*<br/>
Odwołanie do identyfikatora interfejsu.

*ppv*<br/>
Jeśli operacja się powiedzie, wskaźnik do interfejsu określonego przez *riid* lub *iid*.

*IID*<br/>
Odwołanie do identyfikatora interfejsu.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

### <a name="remarks"></a>Uwagi

Pobiera wskaźnik do określonego interfejsu.

## <a name="casttounknown"></a>ImplementsHelper::CastToUnknown

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bazowego `IUnknown` interfejsu.

### <a name="remarks"></a>Uwagi

Pobiera wskaźnik do bazowego `IUnknown` interfejsu dla bieżącego `Implements` struktury.

## <a name="fillarraywithiid"></a>ImplementsHelper::FillArrayWithIid

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>Parametry

*index*<br/>
Liczony od zera indeks, który wskazuje element początkowy tablicy do wykonania tej operacji. Po zakończeniu tej operacji, *indeksu* jest zwiększana o 1.

*IID*<br/>
Tablica typu IID.

### <a name="remarks"></a>Uwagi

Wstawia identyfikator interfejsu określonego przez bieżący parametr szablonu zerowego do elementu określonej tablicy.

## <a name="iidcount"></a>ImplementsHelper::IidCount

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Uwagi

Przechowuje liczbę zaimplementowanego interfejsu identyfikatorów w bieżącym `Implements` obiektu.
