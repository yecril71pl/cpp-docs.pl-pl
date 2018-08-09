---
title: AsyncBase::get_Id, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Id
dev_langs:
- C++
helpviewer_keywords:
- get_Id method
ms.assetid: 591d8366-ea76-4deb-9278-9d3bc394a42b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab02da2dcae788e5eb4b1db15508d2f272ec546a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651561"
---
# <a name="asyncbasegetid-method"></a>AsyncBase::get_Id — Metoda
Pobiera uchwyt operację asynchroniczną.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHOD(  
   get_Id  
)(unsigned int *id) override;  
```  
  
### <a name="parameters"></a>Parametry  
 *id*  
 Lokalizacja, gdzie ma być przechowywany uchwytu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda implementuje `IAsyncInfo::get_Id`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)