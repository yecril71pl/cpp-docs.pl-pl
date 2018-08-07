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
ms.openlocfilehash: a54b61902c8994397c7bd6effa74a90d43c7e512
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39568644"
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose — Metoda
Zamyka bieżące **HandleT** obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
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