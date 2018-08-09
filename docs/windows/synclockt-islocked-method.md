---
title: SyncLockT::IsLocked, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: a81fea43-f99a-4708-812a-7fd6af500d3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4609866b25f574f34b620d81de3a21d6b608db6
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020328"
---
# <a name="synclocktislocked-method"></a>SyncLockT::IsLocked — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
bool IsLocked() const;  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli **SyncLockT** obiektu jest zablokowany; w przeciwnym razie **false**.  
  
## <a name="remarks"></a>Uwagi  
 Wskazuje, czy bieżący **SyncLockT** obiekt posiada zasób; czyli, **SyncLockT** obiekt jest *zablokowane*.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Zobacz też  
 [SyncLockT, klasa](../windows/synclockt-class.md)