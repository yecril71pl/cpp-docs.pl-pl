---
title: accumulate (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::accumulate
dev_langs:
- C++
helpviewer_keywords:
- accumulate function [STL/CLR]
ms.assetid: b80e1ef1-1858-4c1d-817b-c42ad1f17a2f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d9fefc3e7e7a2838891488996518b405972ba0f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="accumulate-stlclr"></a>accumulate (STL/CLR)
Oblicza sumę wszystkich elementów w określonym zakresie m.in. niektóre wartości początkowej przez obliczanie sum częściowych kolejnych lub oblicza wynik kolejne wyniki częściowe podobnie uzyskany przy użyciu określonej operacji binarnych sumą.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _Ty> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);  
template<class _InIt, class _Ty, class _Fn2> inline  
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja liczbowa standardowa biblioteka C++ `accumulate`. Aby uzyskać więcej informacji, zobacz [accumulate](../standard-library/numeric-functions.md#accumulate).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/liczbowe >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)