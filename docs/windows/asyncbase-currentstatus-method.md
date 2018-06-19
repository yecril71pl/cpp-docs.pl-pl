---
title: AsyncBase::CurrentStatus — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 75b9a07fd88caa9db7f2f145069b0d8857b79fe9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859693"
---
# <a name="asyncbasecurrentstatus-method"></a>AsyncBase::CurrentStatus — Metoda
Pobiera stan bieżącego operację asynchroniczną.  
  
## <a name="syntax"></a>Składnia  
  
```  
inline void CurrentStatus(  
   Details::AsyncStatusInternal *status  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `status`  
 Lokalizacja, w którym ta operacja przechowuje przy bieżącym stanie.  
  
## <a name="remarks"></a>Uwagi  
 Ta operacja jest bezpieczne wątkowo.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Asyncbase — klasa](../windows/asyncbase-class.md)   
 [AsyncStatusInternal, wyliczenie](../windows/asyncstatusinternal-enumeration.md)