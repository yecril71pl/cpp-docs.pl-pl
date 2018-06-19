---
title: Synclockt::synclockt — Konstruktor | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: c3353df1a73821a2009aeba2367f1892b06aba5b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889847"
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
  
#### <a name="parameters"></a>Parametry  
 `other`  
 R-wartości — odwołanie do innego obiektu SyncLockT.  
  
 `sync`  
 Odwołanie do innego obiektu synclockwithstatust —.  
  
## <a name="remarks"></a>Uwagi  
 Inicjuje nowe wystąpienie klasy SyncLockT.  
  
 Pierwszy Konstruktor inicjuje bieżącego obiektu SyncLockT z innego obiektu SyncLockT określonej przez parametr `other`, a następnie unieważnia obiektu synclockt —. Drugi Konstruktor jest `protected`i inicjuje bieżącego obiektu synclockt — nieprawidłowy stan.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Zobacz też  
 [SyncLockT, klasa](../windows/synclockt-class.md)