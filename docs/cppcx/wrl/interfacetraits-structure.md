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
ms.openlocfilehash: c08c6e8bbcc16120dd44da69a2933fc3ec42f387
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216573"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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
W `RuntimeClass` przypadku `Implements` `ChainInterfaces` interfejsu, który nie znajduje się na liście obsługiwanych identyfikatorów interfejsów.

## <a name="remarks"></a>Uwagi

Implementuje typowe cechy interfejsu.

Drugi szablon jest specjalizacją dla maskowanych interfejsów. Trzeci szablon jest specjalizacją dla parametrów Nil.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a><a name="public-typedefs"></a>Publiczne definicje typów

Nazwa   | Opis
------ | ------------------------------------------
`Base` | Synonim dla parametru szablonu *I0* .

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                   | Opis
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits:: CanCastTo —](#cancastto)               | Wskazuje, czy określony wskaźnik może być rzutowany na wskaźnik do `Base` .
[InterfaceTraits:: CastToBase —](#casttobase)             | Rzutuje określony wskaźnik na wskaźnik `Base` .
[InterfaceTraits:: CastToUnknown —](#casttounknown)       | Rzutuje określony wskaźnik na wskaźnik `IUnknown` .
[InterfaceTraits:: FillArrayWithIid —](#fillarraywithiid) | Przypisuje identyfikator interfejsu `Base` do elementu tablicy określonego przez argument indeksu.
[InterfaceTraits:: Verify](#verify)                     | Weryfikuje, które `Base` jest prawidłowo wyprowadzane.

### <a name="public-constants"></a>Stałe publiczne

Nazwa                                   | Opis
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits:: IidCount —](#iidcount) | Przechowuje liczbę identyfikatorów interfejsów skojarzonych z bieżącym `InterfaceTraits` obiektem.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`InterfaceTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implementuje. h

**Przestrzeń nazw:** Microsoft:: WRL::D etails

## <a name="interfacetraitscancastto"></a><a name="cancastto"></a>InterfaceTraits:: CanCastTo —

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

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

*riid*<br/>
Identyfikator interfejsu `Base` .

*ppv*<br/>
Jeśli ta operacja zakończy się pomyślnie, *PPV* wskazuje interfejs określony przez `Base` . W przeciwnym razie *PPV* jest ustawiony na **`nullptr`** .

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli ta operacja zakończyła się pomyślnie i *PTR* jest rzutowany na wskaźnik do `Base` ; w przeciwnym razie, **`false`** .

### <a name="remarks"></a>Uwagi

Wskazuje, czy określony wskaźnik może być rzutowany na wskaźnik do `Base` .

Aby uzyskać więcej informacji na temat `Base` , zobacz sekcję [publiczne definicje](#public-typedefs) .

## <a name="interfacetraitscasttobase"></a><a name="casttobase"></a>InterfaceTraits:: CastToBase —

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru *PTR*.

*ptr*<br/>
Wskaźnik do typu *T*.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `Base` .

### <a name="remarks"></a>Uwagi

Rzutuje określony wskaźnik na wskaźnik `Base` .

Aby uzyskać więcej informacji na temat `Base` , zobacz sekcję [publiczne definicje](#public-typedefs) .

## <a name="interfacetraitscasttounknown"></a><a name="casttounknown"></a>InterfaceTraits:: CastToUnknown —

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru *PTR*.

*ptr*<br/>
Wskaźnik do typu *T*.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do elementu IUnknown, z którego `Base` pochodzi.

### <a name="remarks"></a>Uwagi

Rzutuje określony wskaźnik na wskaźnik `IUnknown` .

Aby uzyskać więcej informacji na temat `Base` , zobacz sekcję [publiczne definicje](#public-typedefs) .

## <a name="interfacetraitsfillarraywithiid"></a><a name="fillarraywithiid"></a>InterfaceTraits:: FillArrayWithIid —

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*indeks*<br/>
Wskaźnik do pola, które zawiera wartość indeksu równą zero.

*IID*<br/>
Tablica identyfikatorów interfejsów.

### <a name="remarks"></a>Uwagi

Przypisuje identyfikator interfejsu `Base` do elementu tablicy określonego przez argument indeksu.

W przeciwieństwie do nazwy tego interfejsu API modyfikowany jest tylko jeden element array; to nie jest cała tablica.

Aby uzyskać więcej informacji na temat `Base` , zobacz sekcję [publiczne definicje](#public-typedefs) .

## <a name="interfacetraitsiidcount"></a><a name="iidcount"></a>InterfaceTraits:: IidCount —

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Uwagi

Przechowuje liczbę identyfikatorów interfejsów skojarzonych z bieżącym `InterfaceTraits` obiektem.

## <a name="interfacetraitsverify"></a><a name="verify"></a>InterfaceTraits:: Verify

Obsługuje infrastrukturę WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Uwagi

Weryfikuje, które `Base` jest prawidłowo wyprowadzane.

Aby uzyskać więcej informacji na temat `Base` , zobacz sekcję [publiczne definicje](#public-typedefs) .
