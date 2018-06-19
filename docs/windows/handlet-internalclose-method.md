---
title: HandleT::InternalClose — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 7b0aef97645d515a03dcf2cab90eedc06f07971c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874148"
---
# <a name="handletinternalclose-method"></a>HandleT::InternalClose — Metoda
Zamyka bieżący obiekt handlet —.  
  
## <a name="syntax"></a>Składnia  
  
```  
virtual bool InternalClose();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli bieżący handlet — zamknięty pomyślnie; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 InternalClose() jest chroniony.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [HandleT, klasa](../windows/handlet-class.md)