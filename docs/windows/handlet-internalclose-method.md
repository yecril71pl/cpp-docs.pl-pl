---
title: HandleT::InternalClose, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::InternalClose
dev_langs:
- C++
helpviewer_keywords:
- InternalClose method
ms.assetid: fe693c02-aa1f-4e00-8bdd-a0d7d736da0b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2190a8e85f81062cc1167aa844fccf4afc819bc9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648805"
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose — Metoda
Zamyka bieżące **HandleT** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
virtual bool InternalClose();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli bieżące **HandleT** zamknięta pomyślnie; w przeciwnym razie **false**.  
  
## <a name="remarks"></a>Uwagi  
 **InternalClose()** jest **chronione**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HandleT, klasa](../windows/handlet-class.md)