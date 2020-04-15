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
ms.openlocfilehash: e33842f574df5617fb40c5b3f6bb8324d5ba7c1e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371396"
---
# <a name="implementshelper-structure"></a>ImplementsHelper — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
template <typename RuntimeClassFlagsT, typename ILst, bool IsDelegateToClass>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Parametry

*Środowisko uruchomienioweClassFlagsT*<br/>
Pole flag określające co najmniej jeden wyliczaratorów [RuntimeClassType.](runtimeclasstype-enumeration.md)

*ILst ( ILst )*<br/>
Lista identyfikatorów interfejsu.

*Klasa IsDelegateTo*<br/>
Określ **wartość true,** jeśli bieżące wystąpienie `Implements` jest klasą podstawową pierwszego identyfikatora interfejsu w *ILst;* w przeciwnym razie **false**.

## <a name="remarks"></a>Uwagi

Pomaga zaimplementować [implementuje](implements-structure.md) strukturę.

Ten szablon przechodzi przez listę interfejsów i dodaje je jako klasy `QueryInterface`podstawowe oraz jako informacje niezbędne do włączenia .

## <a name="members"></a>Elementy członkowskie

### <a name="protected-methods"></a>Metody chronione

Nazwa                                                    | Opis
------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------
[ImplementsHelper::CanCastTo](#cancastto)               | Pobiera wskaźnik do określonego identyfikatora interfejsu.
[ImplementsHelper::CastToUnknown](#casttounknown)       | Pobiera wskaźnik do `IUnknown` interfejsu źródłowego `Implements` dla bieżącej struktury.
[ImplementsHelper::FillArrayWithIid](#fillarraywithiid) | Wstawia identyfikator interfejsu określony przez bieżący parametr szablonu zerowego do określonego elementu tablicy.
[ImplementsHelper::IidCount](#iidcount)                 | Przechowuje liczbę zaimplementowanych identyfikatorów `Implements` interfejsu w bieżącym obiekcie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`ImplementsHelper`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="implementshelpercancastto"></a><a name="cancastto"></a>ImplementsHelper::CanCastTo

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

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

*Riid*<br/>
Odwołanie do identyfikatora interfejsu.

*Ppv*<br/>
Jeśli ta operacja zakończy się pomyślnie, wskaźnik do interfejsu określonego przez *riid* lub *iid*.

*Iid*<br/>
Odwołanie do identyfikatora interfejsu.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

### <a name="remarks"></a>Uwagi

Pobiera wskaźnik do określonego identyfikatora interfejsu.

## <a name="implementshelpercasttounknown"></a><a name="casttounknown"></a>ImplementsHelper::CastToUnknown

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `IUnknown` interfejsu źródłowego.

### <a name="remarks"></a>Uwagi

Pobiera wskaźnik do `IUnknown` interfejsu źródłowego `Implements` dla bieżącej struktury.

## <a name="implementshelperfillarraywithiid"></a><a name="fillarraywithiid"></a>ImplementsHelper::FillArrayWithIid

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
void FillArrayWithIid(
   _Inout_ unsigned long *index,
   _Inout_ IID* iids) throw();
```

### <a name="parameters"></a>Parametry

*Indeks*<br/>
Indeks od zera, który wskazuje początkowy element tablicy dla tej operacji. Po zakończeniu tej operacji *indeks* jest zwiększany o 1.

*iids*<br/>
Tablica identyfikatorów typu ID.

### <a name="remarks"></a>Uwagi

Wstawia identyfikator interfejsu określony przez bieżący parametr szablonu zerowego do określonego elementu tablicy.

## <a name="implementshelperiidcount"></a><a name="iidcount"></a>ImplementsHelper::IidCount

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
static const unsigned long IidCount;
```

### <a name="remarks"></a>Uwagi

Przechowuje liczbę zaimplementowanych identyfikatorów `Implements` interfejsu w bieżącym obiekcie.
