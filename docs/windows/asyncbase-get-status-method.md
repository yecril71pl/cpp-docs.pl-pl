---
title: AsyncBase::get_Status, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Status
dev_langs:
- C++
helpviewer_keywords:
- get_Status method
ms.assetid: 9823ecb9-212e-471d-b76f-7b8f21208905
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b49e7cbd30445250bdf0710973ba65e47823b36c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652256"
---
# <a name="asyncbasegetstatus-method"></a>AsyncBase::get_Status — Metoda
Pobiera wartość, która wskazuje stan operacji asynchronicznej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHOD(  
   get_Status  
)(AsyncStatus *status) override;  
```  
  
### <a name="parameters"></a>Parametry  
 *status*  
 Lokalizacja, w których stan ma być przechowywany. Aby uzyskać więcej informacji, zobacz `Windows::Foundation::AsyncStatus` wyliczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda implementuje `IAsyncInfo::get_Status`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)