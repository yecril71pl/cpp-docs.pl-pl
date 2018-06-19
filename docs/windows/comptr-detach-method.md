---
title: ComPtr::Detach — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: b9016775-1ade-4581-be1f-0d6f9c2ca658
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: afa5976d26351ed3022c58fa8226b6038fa816c0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883596"
---
# <a name="comptrdetach-method"></a>ComPtr::Detach — Metoda
Powoduje to usunięcie `ComPtr` obiektu z interfejsu, który reprezentuje.  
  
## <a name="syntax"></a>Składnia  
  
```  
T* Detach();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu, który był reprezentowany przez to `ComPtr` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)