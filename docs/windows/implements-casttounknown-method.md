---
title: Implements::CastToUnknown — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: ca3324f7-4136-406b-8698-7389f4f3d3c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 857d13736a92bbbc2c6f1228b3444081ffc18de5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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