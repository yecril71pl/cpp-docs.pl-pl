---
title: InterfaceTraits — Struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
- implements/Microsoft::WRL::Details::InterfaceTraits::IidCount
- implements/Microsoft::WRL::Details::InterfaceTraits::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::InterfaceTraits structure
- Microsoft::WRL::Details::InterfaceTraits::CanCastTo method
- Microsoft::WRL::Details::InterfaceTraits::CastToBase method
- Microsoft::WRL::Details::InterfaceTraits::CastToUnknown method
- Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid method
- Microsoft::WRL::Details::InterfaceTraits::IidCount constant
- Microsoft::WRL::Details::InterfaceTraits::Verify method
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
ms.openlocfilehash: e8222ccaca9572331412b90e696829568eedcf8e
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335052"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits — Struktura

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template<typename I0>
struct __declspec(novtable) InterfaceTraits;

template<typename CloakedType>
struct __declspec(novtable) InterfaceTraits<
    CloakedIid<CloakedType>
>;

template<>
struct __declspec(novtable) InterfaceTraits<Nil>;
```

### <a name="parameters"></a>Parametry

*I0*<br/>
Nazwa interfejsu.

*CloakedType*<br/>
Aby uzyskać `RuntimeClass`, `Implements` i `ChainInterfaces`, interfejs, który nie będzie na liście obsługiwanych identyfikatorami interfejsu.

## <a name="remarks"></a>Uwagi

Implementuje typowe cechy interfejsu.

Drugi szablon jest specjalizacją osłonięty interfejsów. Trzeci szablon jest specjalizacją zero parametrów.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

Nazwa   | Opis
------ | ------------------------------------------
`Base` | Synonim dla *I0* parametru szablonu.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                   | Opis
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits::CanCastTo](#cancastto)               | Wskazuje, czy określony wskaźnik może być rzutowany na wskaźnik do `Base`.
[InterfaceTraits::CastToBase](#casttobase)             | Rzutuje określony wskaźnik do wskaźnika do `Base`.
[InterfaceTraits::CastToUnknown](#casttounknown)       | Rzutuje określony wskaźnik do wskaźnika do `IUnknown`.
[InterfaceTraits::FillArrayWithIid](#fillarraywithiid) | Przypisuje identyfikator interfejsu `Base` do elementu tablicy, określonego przez argument indeksu.
[InterfaceTraits::Verify](#verify)                     | Sprawdza, czy `Base` wywodzi się poprawnie.

### <a name="public-constants"></a>Publiczne stałe

Nazwa                                   | Opis
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits::IidCount](#iidcount) | Przechowuje liczbę interfejsu identyfikatorów skojarzonych z bieżącym `InterfaceTraits` obiektu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`InterfaceTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="cancastto"></a>InterfaceTraits::CanCastTo

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Nazwa wskaźnika do typu.

*Parametr riid*<br/>
Identyfikator interfejsu `Base`.

*ppv*<br/>
Jeśli operacja zakończy się pomyślnie, *ppv* wskazuje interfejs określony przez `Base`. W przeciwnym razie *ppv* ustawiono `nullptr`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli operacja zakończy się pomyślnie i *ptr* jest rzutowany na wskaźnik do `Base`; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Wskazuje, czy określony wskaźnik może być rzutowany na wskaźnik do `Base`.

Aby uzyskać więcej informacji na temat `Base`, zobacz [publiczne definicje typów](#public-typedefs) sekcji.

## <a name="casttobase"></a>InterfaceTraits::CastToBase

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru *ptr*.

*ptr*<br/>
Wskaźnik do typu *T*.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `Base`.

### <a name="remarks"></a>Uwagi

Rzutuje określony wskaźnik do wskaźnika do `Base`.

Aby uzyskać więcej informacji na temat `Base`, zobacz [publiczne definicje typów](#public-typedefs) sekcji.

## <a name="casttounknown"></a>InterfaceTraits::CastToUnknown

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru *ptr*.

*ptr*<br/>
Wskaźnik do typu *T*.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do IUnknown, z którego `Base` pochodzi.

### <a name="remarks"></a>Uwagi

Rzutuje określony wskaźnik do wskaźnika do `IUnknown`.

Aby uzyskać więcej informacji na temat `Base`, zobacz [publiczne definicje typów](#public-typedefs) sekcji.

## <a name="fillarraywithiid"></a>InterfaceTraits::FillArrayWithIid

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*index*<br/>
Wskaźnik do pola, które zawiera wartość indeksu zaczynającego się od zera.

*IID*<br/>
Tablica identyfikatorów interfejsu.

### <a name="remarks"></a>Uwagi

Przypisuje identyfikator interfejsu `Base` do elementu tablicy, określonego przez argument indeksu.

Sprzecznie nazwę tego interfejsu API tylko jedna tablica element zostanie zmodyfikowany; nie macierz w całości.

Aby uzyskać więcej informacji na temat `Base`, zobacz [publiczne definicje typów](#public-typedefs) sekcji.

## <a name="iidcount"></a>InterfaceTraits::IidCount

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Uwagi

Przechowuje liczbę interfejsu identyfikatorów skojarzonych z bieżącym `InterfaceTraits` obiektu.

## <a name="verify"></a>InterfaceTraits::Verify

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Uwagi

Sprawdza, czy `Base` wywodzi się poprawnie.

Aby uzyskać więcej informacji na temat `Base`, zobacz [publiczne definicje typów](#public-typedefs) sekcji.
