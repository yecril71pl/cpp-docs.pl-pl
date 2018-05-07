---
title: stable_sort — (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::stable_sort
dev_langs:
- C++
helpviewer_keywords:
- stable_sort function [STL/CLR]
ms.assetid: c28fc2df-c68b-4923-ac16-9f8edd926fbb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4f3e4370a00219f438964de5da0853285ac73a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="stablesort-stlclr"></a>stable_sort (STL/CLR)
Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryterium sortowania określonego przez binarny predykat i zachowuje względną kolejność elementów równoważnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _BidIt> inline  
    void stable_sort(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    void stable_sort(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `stable_sort`. Aby uzyskać więcej informacji, zobacz [stable_sort —](../standard-library/algorithm-functions.md#stable_sort).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)