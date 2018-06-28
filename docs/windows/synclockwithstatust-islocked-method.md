---
title: SyncLockWithStatusT::IsLocked — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::IsLocked
dev_langs:
- C++
helpviewer_keywords:
- IsLocked method
ms.assetid: e1b75b7b-c145-471a-aa5d-71abf31f5990
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a564c4223b09d9295ff0ac3159e165944c4d885d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33892556"
---
# <a name="synclockwithstatustislocked-method"></a>SyncLockWithStatusT::IsLocked — Metoda
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
bool IsLocked() const;  
```  
  
## <a name="remarks"></a>Uwagi  
 Wskazuje, czy bieżący obiekt synclockwithstatust — jest właścicielem zasobu; synclockwithstatust — obiektu jest *zablokowany*.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli obiekt synclockwithstatust — jest zablokowany; w przeciwnym razie **false**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Zobacz też  
 [SyncLockWithStatusT, klasa](../windows/synclockwithstatust-class.md)