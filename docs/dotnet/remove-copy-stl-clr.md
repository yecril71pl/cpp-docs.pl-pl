---
title: remove_copy (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::remove_copy
dev_langs:
- C++
helpviewer_keywords:
- remove_copy function [STL/CLR]
ms.assetid: 602fd8e3-26f7-491f-bf2c-cddf269f9807
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f119ff86304a125fc9d0012efef3683aa649bf06
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33161197"
---
# <a name="removecopy-stlclr"></a>remove_copy (STL/CLR)
Kopiuje elementy z zakresu źródłowego do zakresu docelowego, z tym wyjątkiem, że elementy o określonej wartości nie są kopiowane, bez naruszania kolejności pozostałych elementów i zwracania końca nowego zakresu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _OutIt, class _Ty> inline  
    _OutIt remove_copy(_InIt _First, _InIt _Last,  
        _OutIt _Dest, const _Ty% _Val);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `remove_copy`. Aby uzyskać więcej informacji, zobacz [remove_copy](../standard-library/algorithm-functions.md#remove_copy).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)