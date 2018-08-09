---
title: SyncLockWithStatusT::SyncLockWithStatusT, Konstruktor | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 21ce2054cabf257594cb3fa376236b9a1e504a59
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647758"
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
  
### <a name="parameters"></a>Parametry  
 *other*  
 Odwołanie rvalue, do innego **synclockwithstatust —** obiektu.  
  
 *sync*  
 Odwołanie do innego **synclockwithstatust —** obiektu.  
  
 *status*  
 Wartość [status_ — element](../windows/synclockwithstatust-status-data-member.md) element członkowski danych *innych* parametru lub *synchronizacji* parametru.  
  
## <a name="remarks"></a>Uwagi  
 Inicjuje nowe wystąpienie klasy **synclockwithstatust —** klasy.  
  
 Pierwszy Konstruktor inicjuje bieżące **synclockwithstatust —** obiektu z innego **synclockwithstatust —** określony przez parametr *innych*, a następnie druga unieważnia **synclockwithstatust —** obiektu. Drugi Konstruktor jest **chronione**i inicjuje bieżące **synclockwithstatust —** obiektu nieprawidłowym stanie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Zobacz też  
 [Synclockwithstatust — klasa](../windows/synclockwithstatust-class.md)   
 [SyncLockWithStatusT::GetStatus, metoda](../windows/synclockwithstatust-getstatus-method.md)