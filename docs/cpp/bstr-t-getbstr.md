---
title: _bstr_t::GetBSTR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetBSTR
dev_langs:
- C++
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f2c9903170f62652357264a3ea2de0839496e9e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR
**Microsoft Specific**  
  
 Wskazuje początek `BSTR` opakowane przez `_bstr_t`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
BSTR& GetBSTR( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Początek `BSTR` opakowane przez `_bstr_t`.  
  
## <a name="remarks"></a>Uwagi  
 `GetBSTR` dotyczy wszystkich `_bstr_t` obiekty tego udziału `BSTR`. Więcej niż jeden `_bstr_t` mogą udostępniać `BSTR` przy użyciu konstruktora kopiującego i i `operator=`.  
  
## <a name="example"></a>Przykład  
 Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) na przykład za pomocą `GetBSTR`.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_bstr_t, klasa](../cpp/bstr-t-class.md)