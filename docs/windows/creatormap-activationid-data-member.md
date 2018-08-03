---
title: CreatorMap::activationId, składowa danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap::activationId
dev_langs:
- C++
helpviewer_keywords:
- activationId data member
ms.assetid: 77518b76-6e6a-4b48-8e2e-a4c7c67769e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70a331bbbf34a623b02e9d8bc9aa0b80fbee2216
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467134"
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
 *Identyfikator klasy*  
 Identyfikator interfejsu.  
  
 *getRuntimeName*  
 Funkcja, która pobiera nazwę środowiska uruchomieniowego Windows obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Reprezentuje identyfikator obiektu, który jest identyfikowany przez identyfikator klasy klasycznego modelu COM lub nazwę środowiska wykonawczego Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Creatormap — struktura](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)