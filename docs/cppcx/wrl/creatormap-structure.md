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
ms.openlocfilehash: 44d06f317661059bea92d8c6f27955606a964bb7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787306"
---
# <a name="creatormap-structure"></a>CreatorMap — Struktura

Obsługuje infrastrukturę Biblioteka szablonów C++ środowiska wykonawczego Windows i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Uwagi

Zawiera informacje o sposobie inicjowania, rejestrować i wyrejestrowywać obiektów.

`CreatorMap` zawiera następujące informacje:

- Jak zainicjować, rejestrować i wyrejestrowywać obiektów.

- Sposób porównywania danych aktywacji w zależności od fabrykę klasycznego modelu COM lub środowiska wykonawczego Windows.

- Informacje o fabryce pamięci podręcznej i nazwę serwera dla interfejsu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

Nazwa                                          | Opis
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[CreatorMap::activationId](#activationid)     | Reprezentuje identyfikator obiektu, który jest identyfikowany przez identyfikator klasy klasycznego modelu COM lub nazwę środowiska wykonawczego Windows.
[CreatorMap::factoryCache](#factorycache)     | Przechowuje wskaźnik do pamięci podręcznej fabryki dla `CreatorMap`.
[CreatorMap::factoryCreator](#factorycreator) | Tworzy fabrykę dla określonego `CreatorMap`.
[CreatorMap::serverName](#servername)         | Przechowuje nazwę serwera dla `CreatorMap`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CreatorMap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="activationid"></a>CreatorMap::activationId

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>Parametry

*Identyfikator klasy*<br/>
Identyfikator interfejsu.

*getRuntimeName*<br/>
Funkcja, która pobiera nazwę środowiska uruchomieniowego Windows obiektu.

### <a name="remarks"></a>Uwagi

Reprezentuje identyfikator obiektu, który jest identyfikowany przez identyfikator klasy klasycznego modelu COM lub nazwę środowiska wykonawczego Windows.

## <a name="factorycache"></a>CreatorMap::factoryCache

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>Uwagi

Przechowuje wskaźnik do pamięci podręcznej fabryki dla `CreatorMap`.

## <a name="factorycreator"></a>CreatorMap::factoryCreator

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>Parametry

*currentflags*<br/>
Jedną z [RuntimeClassType](runtimeclasstype-enumeration.md) modułów wyliczających.

*entry*<br/>
Creatormap —.

*iidClassFactory*<br/>
Identyfikator interfejsu fabrykę klas.

*Fabryka*<br/>
Po zakończeniu tej operacji adres fabrykę klas.

### <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

### <a name="remarks"></a>Uwagi

Tworzy fabrykę dla określonego creatormap —.

## <a name="servername"></a>CreatorMap::serverName

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>Uwagi

Przechowuje nazwę serwera dla creatormap —.
