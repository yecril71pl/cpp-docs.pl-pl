---
title: "ComPtr::ReleaseAndGetAddressOf — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
dev_langs: C++
helpviewer_keywords: ReleaseAndGetAddressOf method
ms.assetid: 3751dcb4-d50e-432c-89e4-e736be34d434
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b6711cc93071c1e260a5d216a6ad21add9c00540
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Comptr::ptr_ — członek danych](../windows/comptr-ptr-data-member.md)