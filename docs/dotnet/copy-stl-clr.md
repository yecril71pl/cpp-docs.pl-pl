---
title: Kopiowanie (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::copy
dev_langs:
- C++
helpviewer_keywords:
- copy function [STL/CLR]
ms.assetid: f6738535-fde6-446e-a797-bf2b457c2bff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6946868f80a3a655acf32eba80e2fc6f95c0cd71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="copy-stlclr"></a>copy (STL/CLR)
Przypisuje wartości elementów z zakresu źródłowego do zakresu docelowego, iterując przez sekwencję źródłową elementów oraz przypisując im nowe pozycje w kierunku do przodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _OutIt> inline  
    _OutIt copy(_InIt _First, _InIt _Last, _OutIt _Dest);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `copy`. Aby uzyskać więcej informacji, zobacz [kopiowania](http://msdn.microsoft.com/Library/f1fec7da-e01b-40f1-b5bd-6b81e304cae1).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)