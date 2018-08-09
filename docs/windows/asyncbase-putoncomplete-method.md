---
title: AsyncBase::PutOnComplete, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnComplete
dev_langs:
- C++
helpviewer_keywords:
- PutOnComplete method
ms.assetid: 1c469ff9-b2df-4637-bf05-01a617043149
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e982e6f053b207b1d57ed5c0df483a9d9ab778eb
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646975"
---
# <a name="asyncbaseputoncomplete-method"></a>AsyncBase::PutOnComplete — Metoda
Ustawia adres procedury obsługi zdarzeń zakończenia z podaną wartością.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHOD(  
   PutOnComplete  
)(TComplete* completeHandler);  
```  
  
### <a name="parameters"></a>Parametry  
 *completeHandler*  
 Adres, do którego program obsługi zdarzeń zakończenia jest ustawiony.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)