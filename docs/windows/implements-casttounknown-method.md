---
title: "Implements::CastToUnknown — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Implements::CastToUnknown
dev_langs: C++
helpviewer_keywords: CastToUnknown method
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ced646ecfe5989dd59b99ef3eb6dff48e4ddb74c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="implementscasttounknown-method"></a>Implements::CastToUnknown — Metoda
Pobiera wskaźnik do podstawowego interfejsu IUnknown.  
  
## <a name="syntax"></a>Składnia  
  
```  
__forceinline IUnknown* CastToUnknown();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta operacja zawsze kończy się powodzeniem i zwraca wskaźnik IUnknown.  
  
## <a name="remarks"></a>Uwagi  
 Funkcja pomocnika wewnętrznego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** implements.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Implements, struktura](../windows/implements-structure.md)