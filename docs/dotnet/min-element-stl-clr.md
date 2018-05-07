---
title: min_element (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::min_element
dev_langs:
- C++
helpviewer_keywords:
- min_element function [STL/CLR]
ms.assetid: 2a9c6828-9722-454f-9c10-d4a184d4d21b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 27bfa9632a4145bc93d20a43b873bdfcdd498a2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="minelement-stlclr"></a>min_element (STL/CLR)
Znajduje pierwsze wystąpienie najmniejszego elementu w określonym zakresie, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt> inline  
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last);  
template<class _FwdIt, class _Pr> inline  
    _FwdIt min_element(_FwdIt _First, _FwdIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `min_element`. Aby uzyskać więcej informacji, zobacz [min_element](../standard-library/algorithm-functions.md#min_element).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)