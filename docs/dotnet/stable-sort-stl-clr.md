---
title: "stable_sort — (STL/CLR) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::stable_sort
dev_langs: C++
helpviewer_keywords: stable_sort function [STL/CLR]
ms.assetid: c28fc2df-c68b-4923-ac16-9f8edd926fbb
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 73632e44b4b2dc11a805e36b371f738ea3eb37e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Algorytm (STL/CLR)](../dotnet/algorithm-stl-clr.md)