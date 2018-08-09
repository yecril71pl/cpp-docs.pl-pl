---
title: AsyncBase::GetOnProgress, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::GetOnProgress
dev_langs:
- C++
helpviewer_keywords:
- GetOnProgress method
ms.assetid: 286ddc9c-3e30-41a2-8e8b-e53d3fb0649d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9446c94039db0ff81826e77d71a2a9539be4b276
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39643150"
---
# <a name="asyncbasegetonprogress-method"></a>AsyncBase::GetOnProgress — Metoda
Kopiuje adres bieżącej obsługi zdarzeń postępu do określonej zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHOD(  
   GetOnProgress  
)(TProgress** progressHandler);  
```  
  
### <a name="parameters"></a>Parametry  
 *progressHandler*  
 Lokalizacja przechowywania adres bieżącej obsługi zdarzeń postępu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [AsyncBase, klasa](../windows/asyncbase-class.md)