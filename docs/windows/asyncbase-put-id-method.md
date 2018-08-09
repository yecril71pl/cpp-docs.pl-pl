---
title: AsyncBase::put_Id, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::put_Id
dev_langs:
- C++
helpviewer_keywords:
- put_Id method
ms.assetid: aebad85f-4774-42de-b625-a9cf5f65cb4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f55896ac0bca162df9f17703225552cdb70c079c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647089"
---
# <a name="asyncbaseputid-method"></a>AsyncBase::put_Id — Metoda
Ustawia uchwyt operację asynchroniczną.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHOD(  
   put_Id  
)(const unsigned int id);  
```  
  
### <a name="parameters"></a>Parametry  
 *id*  
 Dojście wartość różną od zera.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_INVALIDARG lub E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)