---
title: prev_permutation (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::prev_permutation
dev_langs: C++
helpviewer_keywords: prev_permutation function [STL/CLR]
ms.assetid: 5294dbe5-1b5f-4369-a764-067dff86d1e8
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e2023cfda5d434fd7302c66dd1a583186cb11adb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="prevpermutation-stlclr"></a>prev_permutation (STL/CLR)
Zmienia kolejność elementów w zakresie, tak że oryginalna kolejność jest zastąpiona przez leksykograficznie kolejną większą permutację, o ile takowa istnieje, gdzie sens „kolejna” może być określony przez predykat binarny.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _BidIt> inline  
    bool prev_permutation(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    bool prev_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `prev_permutation`. Aby uzyskać więcej informacji, zobacz [prev_permutation](../standard-library/algorithm-functions.md#prev_permutation).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [Algorytm (STL/CLR)](../dotnet/algorithm-stl-clr.md)