---
title: "HString::GetAddressOf — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
dev_langs: C++
ms.assetid: 6050decf-5f99-49f0-9497-1c8192c485ae
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc4c15570b65b62b22f0dd9a7f66f8c244e2bf22
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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