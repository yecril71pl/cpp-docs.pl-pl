---
title: "Creatormap — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
dev_langs: C++
helpviewer_keywords: CreatorMap structure
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c61238a809da49686975acbfb8016996cf5d5c1a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[Creatormap::activationid — członek danych](../windows/creatormap-activationid-data-member.md)|Reprezentuje identyfikator obiektu, który jest identyfikowany przez identyfikator klasy klasycznego modelu COM lub nazwę środowiska wykonawczego systemu Windows.|  
|[Creatormap::factorycache — członek danych](../windows/creatormap-factorycache-data-member.md)|Creatormap — przechowuje wskaźnik do pamięci podręcznej fabryki.|  
|[Creatormap::factorycreator — członek danych](../windows/creatormap-factorycreator-data-member.md)|Tworzy fabrykę dla określonego creatormap —.|  
|[Creatormap::servername — członek danych](../windows/creatormap-servername-data-member.md)|Przechowuje nazwę serwera dla creatormap —.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CreatorMap`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)