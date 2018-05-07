---
title: MAX (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::max
dev_langs:
- C++
helpviewer_keywords:
- max function [STL/CLR]
ms.assetid: bf51aedc-b7a0-4b6c-a76e-fdbc4af042fa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0d06044fd8996682431be0f2fd89ae3059c93f51
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="max-stlclr"></a>max (STL/CLR)
Porównuje dwa obiekty i zwraca większy z nich, gdzie kryterium sortowania może być określone przez predykat binarny.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _Ty> inline  
    const _Ty max(const _Ty% _Left, const _Ty% _Right);  
template<class _Ty, class _Pr> inline  
    const _Ty max(const _Ty% _Left, const _Ty% _Right, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `max`. Aby uzyskać więcej informacji, zobacz [max](../standard-library/algorithm-functions.md#max).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)