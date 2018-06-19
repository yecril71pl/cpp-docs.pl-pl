---
title: ComPtr::ReleaseAndGetAddressOf — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 32d846a1fc41596812ca6e8578f25f9ae8115182
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883802"
---
# <a name="comptrreleaseandgetaddressof-method"></a>ComPtr::ReleaseAndGetAddressOf — Metoda
Zwalnia skojarzony z tym comptr — interfejs, a następnie pobiera adres [ptr_ — element](../windows/comptr-ptr-data-member.md) danych elementu członkowskiego, który zawiera wskaźnik do interfejsu, która została opublikowana.  
  
## <a name="syntax"></a>Składnia  
  
```  
T** ReleaseAndGetAddressOf();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Adres [ptr_ — element](../windows/comptr-ptr-data-member.md) tego comptr — element członkowski danych.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Comptr — klasa](../windows/comptr-class.md)   
 [ComPtr::ptr_, składowa danych](../windows/comptr-ptr-data-member.md)