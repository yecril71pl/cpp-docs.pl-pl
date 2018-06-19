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
ms.openlocfilehash: a6113737d7463354ffa273ced61b190246f63a83
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873287"
---
# <a name="creatormap-structure"></a>CreatorMap — Struktura
Obsługuje infrastrukturę Biblioteka szablonów C++ środowiska wykonawczego systemu Windows i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CreatorMap;  
```  
  
## <a name="remarks"></a>Uwagi  
 Zawiera informacje o sposobie inicjowania, rejestrowanie i wyrejestrowywanie obiektów.  
  
 Creatormap — zawiera następujące informacje:  
  
-   Jak zainicjować, rejestrowanie i wyrejestrowywanie obiektów.  
  
-   Sposób porównywania danych aktywacji w zależności od fabrykę klasycznego modelu COM lub środowiska wykonawczego systemu Windows.  
  
-   Informacje o fabryki pamięci podręcznej i nazwę serwera dla interfejsu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CreatorMap::activationId, składowa danych](../windows/creatormap-activationid-data-member.md)|Reprezentuje identyfikator obiektu, który jest identyfikowany przez identyfikator klasy klasycznego modelu COM lub nazwę środowiska wykonawczego systemu Windows.|  
|[CreatorMap::factoryCache, składowa danych](../windows/creatormap-factorycache-data-member.md)|Creatormap — przechowuje wskaźnik do pamięci podręcznej fabryki.|  
|[CreatorMap::factoryCreator, składowa danych](../windows/creatormap-factorycreator-data-member.md)|Tworzy fabrykę dla określonego creatormap —.|  
|[CreatorMap::serverName, składowa danych](../windows/creatormap-servername-data-member.md)|Przechowuje nazwę serwera dla creatormap —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CreatorMap`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)