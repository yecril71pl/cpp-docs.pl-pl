---
title: HString::GetAddressOf — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
dev_langs:
- C++
ms.assetid: 6050decf-5f99-49f0-9497-1c8192c485ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d4804373045d12c2e251e2de61b7aefd52ec916
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="hstringgetaddressof-method"></a>HString::GetAddressOf — Metoda
Pobiera wskaźnik do podstawowego dojście HSTRING.  
  
## <a name="syntax"></a>Składnia  
  
```  
HSTRING* GetAddressOf() throw()  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do podstawowego dojście HSTRING.  
  
## <a name="remarks"></a>Uwagi  
 Po tej operacji wartość ciągu źródłowego dojścia HSTRING zostanie zniszczony.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [HString, klasa](../windows/hstring-class.md)