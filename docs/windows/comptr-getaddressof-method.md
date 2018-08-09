---
title: ComPtr::GetAddressOf, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::GetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- GetAddressOf method
ms.assetid: 972a41d0-c2ef-4ae3-b2cd-77cc45156ac9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c1be1dd844b08be23312848f007e4a57dbd893b5
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39646988"
---
# <a name="comptrgetaddressof-method"></a>ComPtr::GetAddressOf — Metoda
Pobiera adres [ptr_ — element](../windows/comptr-ptr-data-member.md) element członkowski danych, który zawiera wskaźnik do interfejsu, reprezentowane przez to **ComPtr**.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
T* const* GetAddressOf() const;  
T** GetAddressOf();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Adres zmiennej.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)