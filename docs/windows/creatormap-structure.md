---
title: Creatormap — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
dev_langs:
- C++
helpviewer_keywords:
- CreatorMap structure
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0a622eaa40cedfd7bf22259cf81382290f20f3a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593737"
---
# <a name="creatormap-structure"></a>CreatorMap — Struktura

Obsługuje infrastrukturę Biblioteka szablonów C++ środowiska wykonawczego Windows i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Uwagi

Zawiera informacje o sposobie inicjowania, rejestrować i wyrejestrowywać obiektów.

**Creatormap —** zawiera następujące informacje:

- Jak zainicjować, rejestrować i wyrejestrowywać obiektów.

- Sposób porównywania danych aktywacji w zależności od fabrykę klasycznego modelu COM lub środowiska wykonawczego Windows.

- Informacje o fabryce pamięci podręcznej i nazwę serwera dla interfejsu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CreatorMap::activationId, składowa danych](../windows/creatormap-activationid-data-member.md)|Reprezentuje identyfikator obiektu, który jest identyfikowany przez identyfikator klasy klasycznego modelu COM lub nazwę środowiska wykonawczego Windows.|
|[CreatorMap::factoryCache, składowa danych](../windows/creatormap-factorycache-data-member.md)|Przechowuje wskaźnik do pamięci podręcznej fabryki dla **creatormap —**.|
|[CreatorMap::factoryCreator, składowa danych](../windows/creatormap-factorycreator-data-member.md)|Tworzy fabrykę dla określonego **creatormap —**.|
|[CreatorMap::serverName, składowa danych](../windows/creatormap-servername-data-member.md)|Przechowuje nazwę serwera dla **creatormap —**.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CreatorMap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)