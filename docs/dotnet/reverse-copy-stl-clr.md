---
title: reverse_copy (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::reverse_copy
dev_langs:
- C++
helpviewer_keywords:
- reverse_copy function [STL/CLR]
ms.assetid: 694e577a-0fa8-44f7-adde-6dd9f45adefd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 48c0f333636a365e168cb2782e5f02002cd20e80
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="reversecopy-stlclr"></a>reverse_copy (STL/CLR)
Odwraca kolejność elementów w zakresie źródła podczas kopiowania ich do zakresu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _BidIt, class _OutIt> inline  
    _OutIt reverse_copy(_BidIt _First, _BidIt _Last, _OutIt _Dest);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `reverse_copy`. Aby uzyskać więcej informacji, zobacz [reverse_copy](../standard-library/algorithm-functions.md#reverse_copy).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)