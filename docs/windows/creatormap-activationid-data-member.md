---
title: "Creatormap::activationid — członek danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::CreatorMap::activationId
dev_langs: C++
helpviewer_keywords: activationId data member
ms.assetid: 77518b76-6e6a-4b48-8e2e-a4c7c67769e0
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 912b18ff3e1be04913cb9345e4ac5bde25d2e039
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creatormapactivationid-data-member"></a>CreatorMap::activationId — Członek danych
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
union {   
   const IID* clsid;  
   const wchar_t* (*getRuntimeName)();  
} activationId;  
```  
  
## <a name="parameters"></a>Parametry  
 `clsid`  
 Identyfikatora interfejsu.  
  
 `getRuntimeName`  
 Funkcja, która pobiera nazwę obiektu środowiska wykonawczego systemu Windows.  
  
## <a name="remarks"></a>Uwagi  
 Reprezentuje identyfikator obiektu, który jest identyfikowany przez identyfikator klasy klasycznego modelu COM lub nazwę środowiska wykonawczego systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Creatormap — struktura](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)