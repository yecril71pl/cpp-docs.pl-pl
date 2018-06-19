---
title: Niezgodność (STL/CLR) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::mismatch
dev_langs:
- C++
helpviewer_keywords:
- mismatch function [STL/CLR]
ms.assetid: 77876875-44bb-4476-afd9-390da4eaac16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a374a62e4f2d0ee66a8366d2ca484f7c7b8f6cbc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33131949"
---
# <a name="mismatch-stlclr"></a>mismatch (STL/CLR)
Porównuje dwa zakresy element po elemencie pod względem równości lub odpowiedniości w sensie określonym przez predykat binarny i lokalizuje pierwsze miejsce, w którym występuje różnica.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class _InIt1, class _InIt2> inline  
    _PAIR_TYPE(_InIt1)  
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2);  
template<class _InIt1, class _InIt2, class _Pr> inline  
    _PAIR_TYPE(_InIt1)  
        mismatch(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,  
            _Pr _Pred);  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja działa tak samo jak funkcja standardowa biblioteka C++ `mismatch`. Aby uzyskać więcej informacji, zobacz [niezgodność](../standard-library/algorithm-functions.md#mismatch).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<cliext/algorytm >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Zobacz też  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)