---
title: Asyncbase::currentstatusm metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::CurrentStatus
dev_langs:
- C++
helpviewer_keywords:
- CurrentStatus method
ms.assetid: 26ee4c4a-6525-4a5f-b49c-3ca40c365eb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 36c3f76e3fc137458acddacd834563d845057a24
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646578"
---
# <a name="asyncbasecurrentstatus-method"></a>AsyncBase::CurrentStatus — Metoda
Pobiera stan bieżącej operacji asynchronicznej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
inline void CurrentStatus(  
   Details::AsyncStatusInternal *status  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *status*  
 Lokalizacja, w którym ta operacja zapisuje bieżący stan.  
  
## <a name="remarks"></a>Uwagi  
 Ta operacja jest metodą o bezpiecznych wątkach.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Asyncbase — klasa](../windows/asyncbase-class.md)   
 [AsyncStatusInternal, wyliczenie](../windows/asyncstatusinternal-enumeration.md)