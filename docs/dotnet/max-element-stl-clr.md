---
title: max_element (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::max_element
dev_langs:
- C++
helpviewer_keywords:
- max_element function [STL/CLR]
ms.assetid: c6274bae-1216-4285-b395-254280253dae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 84fb1fb7a3b99889f5a2926fcdb786316dd5abe5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="maxelement-stlclr"></a>max_element (STL/CLR)
Znajduje pierwsze wystąpienie największego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt> inline  
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt max_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `max_element`. Aby uzyskać więcej informacji, zobacz [max_element](../standard-library/algorithm-functions.md#max_element).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)