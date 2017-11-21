---
title: partial_sum (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::partial_sum
dev_langs: C++
helpviewer_keywords: partial_sum function [STL/CLR]
ms.assetid: 845badae-8519-4ac8-9ea7-2b921bac7c51
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d8a92858303af5050706849f7e688d08ad36f321
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="partialsum-stlclr"></a>partial_sum (STL/CLR)
Oblicza szereg sum zakresu wejściowego od pierwszego elementu za pomocą `i`th element i zapisuje wynik każdego kwoty w `i`element th zakresu docelowego lub oblicza wynik uogólniony procedury gdzie operacji sum zastępuje inna operacja określonego pliku binarnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);  
template<class _InIt, class _OutIt, class _Fn2> inline  
    _OutIt partial_sum(_InIt _First, _InIt _Last,  
        _OutIt _Dest, _Fn2 _Func);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja liczbowa standardowa biblioteka C++ `partial_sum`. Aby uzyskać więcej informacji, zobacz [partial_sum](../standard-library/numeric-functions.md#partial_sum).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/liczbowe >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [liczbowe (STL/CLR)](../dotnet/numeric-stl-clr.md)