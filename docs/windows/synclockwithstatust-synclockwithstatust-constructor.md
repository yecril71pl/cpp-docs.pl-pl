---
title: Synclockwithstatust::synclockwithstatust — Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockWithStatusT, constructor
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8f665866a43e45d6526aa33f17c05eacebdd84aa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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