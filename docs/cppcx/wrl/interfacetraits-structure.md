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
ms.openlocfilehash: 17f743a38af3ddc600a55e38905d19868d076a22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371368"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits — Struktura

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

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

*CloakedType (Typ maskowania)*<br/>
Dla `RuntimeClass` `Implements` , `ChainInterfaces`i , interfejs, który nie będzie na liście obsługiwanych identyfikatorów interfejsu.

## <a name="remarks"></a>Uwagi

Implementuje wspólne cechy interfejsu.

Drugi szablon jest specjalizacją dla zamaskowanych interfejsów. Trzeci szablon jest specjalizacją dla parametrów Nil.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a><a name="public-typedefs"></a>Publiczne typedefs

Nazwa   | Opis
------ | ------------------------------------------
`Base` | Synonim parametru szablonu *I0.*

### <a name="public-methods"></a>Metody publiczne

Nazwa                                                   | Opis
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits::CanCastTo](#cancastto)               | Wskazuje, czy określony wskaźnik można rzutować `Base`na wskaźnik do .
[InterfaceTraits::CastToBase](#casttobase)             | Rzutuje określony wskaźnik na `Base`wskaźnik do .
[InterfaceTraits::CastToUnknown](#casttounknown)       | Rzutuje określony wskaźnik na `IUnknown`wskaźnik do .
[InterfaceTraits::FillArrayWithIid](#fillarraywithiid) | Przypisuje identyfikator interfejsu do `Base` elementu tablicy określonego przez argument indeksu.
[InterfaceTraits::Sprawdź](#verify)                     | Sprawdza, `Base` czy jest prawidłowo pochodna.

### <a name="public-constants"></a>Stałe publiczne

Nazwa                                   | Opis
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits::IidCount](#iidcount) | Przechowuje liczbę identyfikatorów interfejsu skojarzonych `InterfaceTraits` z bieżącym obiektem.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`InterfaceTraits`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="interfacetraitscancastto"></a><a name="cancastto"></a>InterfaceTraits::CanCastTo

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parametry

*Ptr*<br/>
Nazwa wskaźnika do typu.

*Riid*<br/>
Identyfikator interfejsu . `Base`

*Ppv*<br/>
Jeśli ta operacja zakończy się pomyślnie, *ppv* wskazuje interfejs określony przez `Base`. W przeciwnym razie *ppv* jest ustawiona na `nullptr`.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli ta operacja zakończy się pomyślnie `Base`i *ptr* jest rzutowy na wskaźnik do ; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Wskazuje, czy określony wskaźnik można rzutować `Base`na wskaźnik do .

Aby uzyskać `Base`więcej informacji na temat , zobacz [Public Typedefs](#public-typedefs) sekcji.

## <a name="interfacetraitscasttobase"></a><a name="casttobase"></a>InterfaceTraits::CastToBase

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru *ptr*.

*Ptr*<br/>
Wskaźnik do typu *T*.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `Base`.

### <a name="remarks"></a>Uwagi

Rzutuje określony wskaźnik na `Base`wskaźnik do .

Aby uzyskać `Base`więcej informacji na temat , zobacz [Public Typedefs](#public-typedefs) sekcji.

## <a name="interfacetraitscasttounknown"></a><a name="casttounknown"></a>InterfaceTraits::CastToUnknown

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru *ptr*.

*Ptr*<br/>
Wskaźnik do wpisywać *T*.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do IUnknown, `Base` z którego pochodzi.

### <a name="remarks"></a>Uwagi

Rzutuje określony wskaźnik na `IUnknown`wskaźnik do .

Aby uzyskać `Base`więcej informacji na temat , zobacz [Public Typedefs](#public-typedefs) sekcji.

## <a name="interfacetraitsfillarraywithiid"></a><a name="fillarraywithiid"></a>InterfaceTraits::FillArrayWithIid

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parametry

*Indeks*<br/>
Wskaźnik do pola, które zawiera wartość indeksu opartego na wartości od zera.

*iids*<br/>
Tablica identyfikatorów interfejsu.

### <a name="remarks"></a>Uwagi

Przypisuje identyfikator interfejsu do `Base` elementu tablicy określonego przez argument indeksu.

W przeciwieństwie do nazwy tego interfejsu API tylko jeden element tablicy jest modyfikowany; nie cała tablica.

Aby uzyskać `Base`więcej informacji na temat , zobacz [Public Typedefs](#public-typedefs) sekcji.

## <a name="interfacetraitsiidcount"></a><a name="iidcount"></a>InterfaceTraits::IidCount

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Uwagi

Przechowuje liczbę identyfikatorów interfejsu skojarzonych `InterfaceTraits` z bieżącym obiektem.

## <a name="interfacetraitsverify"></a><a name="verify"></a>InterfaceTraits::Sprawdź

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Uwagi

Sprawdza, `Base` czy jest prawidłowo pochodna.

Aby uzyskać `Base`więcej informacji na temat , zobacz [Public Typedefs](#public-typedefs) sekcji.
