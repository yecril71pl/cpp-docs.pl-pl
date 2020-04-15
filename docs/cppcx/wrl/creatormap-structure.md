---
title: CreatorMap — Struktura
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
- module/Microsoft::WRL::Details::CreatorMap::activationId
- module/Microsoft::WRL::Details::CreatorMap::factoryCache
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
- module/Microsoft::WRL::Details::CreatorMap::serverName
helpviewer_keywords:
- Microsoft::WRL::Details::CreatorMap structure
- Microsoft::WRL::Details::CreatorMap::activationId data member
- Microsoft::WRL::Details::CreatorMap::factoryCache data member
- Microsoft::WRL::Details::CreatorMap::factoryCreator data member
- Microsoft::WRL::Details::CreatorMap::serverName data member
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
ms.openlocfilehash: 1527f81694d1d809d585f3f6504c0e6433a2c26b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372599"
---
# <a name="creatormap-structure"></a>CreatorMap — Struktura

Obsługuje infrastrukturę biblioteki szablonów środowiska wykonawczego systemu Windows W++ i nie jest przeznaczona do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Uwagi

Zawiera informacje dotyczące inicjowania, rejestrowania i wyrejestrowywać obiekty.

`CreatorMap`zawiera następujące informacje:

- Jak zainicjować, zarejestrować i wyrejestrować obiekty.

- Jak porównać dane aktywacji w zależności od klasycznej fabryki com lub windows runtime.

- Informacje o pamięci podręcznej fabryki i nazwie serwera interfejsu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

Nazwa                                          | Opis
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[CreatorMap::activationId](#activationid)     | Reprezentuje identyfikator obiektu, który jest identyfikowany przez klasyczny identyfikator klasy COM lub nazwę środowiska wykonawczego systemu Windows.
[CreatorMap::factoryCache](#factorycache)     | Przechowuje wskaźnik do pamięci `CreatorMap`podręcznej fabryki dla .
[CreatorMap::factoryCreator](#factorycreator) | Tworzy fabrykę dla `CreatorMap`określonego pliku .
[CreatorMap::nazwa serwera](#servername)         | Przechowuje nazwę serwera `CreatorMap`dla pliku .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CreatorMap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="creatormapactivationid"></a><a name="activationid"></a>CreatorMap::activationId

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
Identyfikator interfejsu.

*getRuntimeName (nazwa)*<br/>
Funkcja pobierająca nazwę środowiska wykonawczego systemu Windows obiektu.

### <a name="remarks"></a>Uwagi

Reprezentuje identyfikator obiektu, który jest identyfikowany przez klasyczny identyfikator klasy COM lub nazwę środowiska wykonawczego systemu Windows.

## <a name="creatormapfactorycache"></a><a name="factorycache"></a>CreatorMap::factoryCache

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>Uwagi

Przechowuje wskaźnik do pamięci `CreatorMap`podręcznej fabryki dla .

## <a name="creatormapfactorycreator"></a><a name="factorycreator"></a>CreatorMap::factoryCreator

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>Parametry

*prądy*<br/>
Jeden z [wyliczaczy RuntimeClassType.](runtimeclasstype-enumeration.md)

*Wpis*<br/>
Mapa twórcy.

*iidClassFactory (iidClassFactory)*<br/>
Identyfikator interfejsu fabryki klasy.

*Fabryki*<br/>
Po zakończeniu operacji adres fabryki klasy.

### <a name="return-value"></a>Wartość zwracana

S_OK, jeśli się powiedzie; w przeciwnym razie HRESULT, który wskazuje błąd.

### <a name="remarks"></a>Uwagi

Tworzy fabrykę dla określonej mapy creatormap.

## <a name="creatormapservername"></a><a name="servername"></a>CreatorMap::nazwa serwera

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>Uwagi

Przechowuje nazwę serwera dla CreatorMap.
