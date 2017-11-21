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
ms.openlocfilehash: 0432a8f5966f6544808ffa4668777d2900ee5066
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Hstring — klasa](../windows/hstring-class.md)