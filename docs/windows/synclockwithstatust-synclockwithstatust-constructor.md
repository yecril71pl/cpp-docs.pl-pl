---
title: "Synclockwithstatust::synclockwithstatust — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dc5be4a37182cb23b47a2511d2e7d5eb0ffa558a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="synclockwithstatustsynclockwithstatust-constructor"></a>SyncLockWithStatusT::SyncLockWithStatusT — Konstruktor
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
SyncLockWithStatusT(  
   _Inout_ SyncLockWithStatusT&& other  
);  
  
explicit SyncLockWithStatusT(  
   typename SyncTraits::Type sync,  
   DWORD status  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `other`  
 R-wartości — odwołanie do innego obiektu synclockwithstatust —.  
  
 `sync`  
 Odwołanie do innego obiektu synclockwithstatust —.  
  
 `status`  
 Wartość [status_ —](../windows/synclockwithstatust-status-data-member.md) elementu członkowskiego danych `other` parametru lub `sync` parametru.  
  
## <a name="remarks"></a>Uwagi  
 Inicjuje nowe wystąpienie klasy synclockwithstatust — klasa.  
  
 Pierwszy Konstruktor inicjuje bieżącego obiektu synclockwithstatust — z innego synclockwithstatust — określonej przez parametr `other`, a następnie unieważnia obiektu synclockwithstatust —. Drugi Konstruktor jest `protected`i inicjuje bieżącego obiektu synclockwithstatust — nieprawidłowy stan.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Zobacz też  
 [Synclockwithstatust — klasa](../windows/synclockwithstatust-class.md)   
 [SyncLockWithStatusT::GetStatus, metoda](../windows/synclockwithstatust-getstatus-method.md)