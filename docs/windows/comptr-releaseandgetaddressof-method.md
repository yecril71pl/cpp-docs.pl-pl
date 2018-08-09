---
title: ComPtr::ReleaseAndGetAddressOf, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- ReleaseAndGetAddressOf method
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3bded6992abc5b22e2c02a3364431a3f68b76ad6
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649851"
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf — Metoda
Zwalnia interfejs skojarzony z tym **ComPtr** i następnie pobiera adres [ptr_ — element](../windows/comptr-ptr-data-member.md) element członkowski danych, który zawiera wskaźnik do interfejsu, który został wydany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
T** ReleaseAndGetAddressOf();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Adres [ptr_ — element](../windows/comptr-ptr-data-member.md) to element członkowski danych **ComPtr**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Comptr — klasa](../windows/comptr-class.md)   
 [ComPtr::ptr_, składowa danych](../windows/comptr-ptr-data-member.md)