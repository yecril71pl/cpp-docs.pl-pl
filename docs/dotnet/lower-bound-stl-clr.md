---
title: lower_bound (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::lower_bound
dev_langs:
- C++
helpviewer_keywords:
- lower_bound function [STL/CLR]
ms.assetid: 841b70b5-1f54-4ecf-8faa-7dda32a24c54
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a2e4cbe940ce9eaaa99725a3d252a0275c4fa84e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="lowerbound-stlclr"></a>lower_bound (STL/CLR)
Znajduje położenie pierwszego elementu w uporządkowanego, który ma wartość mniejszą lub równoważnego określoną wartość, której można określić kryterium porządkowania binarne predykat.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _FwdIt, class _Ty> inline  
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last, const _Ty% _Val);  
template<class _FwdIt, class _Ty, class _Pr> inline  
    _FwdIt lower_bound(_FwdIt _First, _FwdIt _Last,  
        const _Ty% _Val, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `lower_bound`. Aby uzyskać więcej informacji, zobacz [lower_bound](../standard-library/algorithm-functions.md#lower_bound).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)