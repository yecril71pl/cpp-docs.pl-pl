---
title: replace_copy (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::replace_copy
dev_langs:
- C++
helpviewer_keywords:
- replace_copy function [STL/CLR]
ms.assetid: b531b49b-b16d-4b04-8f80-74f43dd496a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a027bbf1374988d79b94585f0d303c7e352ddbee
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="replacecopy-stlclr"></a>replace_copy (STL/CLR)
Sprawdza każdy element w zakresie źródłowym i zastępuje go, jeśli odpowiada określonej wartości, jednocześnie kopiując wynik do nowego zakresu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _InIt, class _OutIt, class _Ty> inline  
    _OutIt replace_copy(_InIt _First, _InIt _Last, _OutIt _Dest,  
        const _Ty% _Oldval, const _Ty% _Newval);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `replace_copy`. Aby uzyskać więcej informacji, zobacz [replace_copy](../standard-library/algorithm-functions.md#replace_copy).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)