---
title: SyncLockT::SyncLockT, Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT
dev_langs:
- C++
helpviewer_keywords:
- SyncLockT, constructor
ms.assetid: 713dfd9f-7369-4d86-b4a0-8b32c184d89b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ceaafd6230e6497ed2b7636ad5070141546cb8d6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648168"
---
# <a name="synclocktsynclockt-constructor"></a>SyncLockT::SyncLockT — Konstruktor
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
SyncLockT(  
   _Inout_ SyncLockT&& other  
);  
  
explicit SyncLockT(  
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *other*  
 Odwołanie rvalue, do innego **SyncLockT** obiektu.  
  
 *sync*  
 Odwołanie do innego `SyncLockWithStatusT` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Inicjuje nowe wystąpienie klasy **SyncLockT** klasy.  
  
 Pierwszy Konstruktor inicjuje bieżące **SyncLockT** obiektu z innego **SyncLockT** obiekt określony przez parametr *innych*, a następnie unieważnia innych  **SyncLockT** obiektu. Drugi Konstruktor jest **chronione**i inicjuje bieżące **SyncLockT** obiektu nieprawidłowym stanie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Zobacz też  
 [SyncLockT, klasa](../windows/synclockt-class.md)