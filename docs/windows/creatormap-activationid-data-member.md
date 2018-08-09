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
ms.openlocfilehash: 3b9fd147f0821e14e825b2a8c0e8d7ad35104fe9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39653017"
---
# <a name="creatormapactivationid-data-member"></a>CreatorMap::activationId — Członek danych
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
union {   
   const IID* clsid;  
   const wchar_t* (*getRuntimeName)();  
} activationId;  
```  
  
### <a name="parameters"></a>Parametry  
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