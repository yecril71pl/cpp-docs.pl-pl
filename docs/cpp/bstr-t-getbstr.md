---
title: _bstr_t::GetBSTR | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetBSTR
dev_langs:
- C++
helpviewer_keywords:
- GetBSTR method [C++]
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 00b2f7f487673c67aa7b681499462ea05a471b48
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="bstrtgetbstr"></a>_bstr_t::GetBSTR
**Dotyczące firmy Microsoft**  
  
 Wskazuje początek `BSTR` opakowane przez `_bstr_t`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
BSTR& GetBSTR( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Początek `BSTR` opakowane przez `_bstr_t`.  
  
## <a name="remarks"></a>Uwagi  
 `GetBSTR`dotyczy wszystkich `_bstr_t` obiekty tego udziału `BSTR`. Więcej niż jeden `_bstr_t` mogą udostępniać `BSTR` przy użyciu konstruktora kopiującego i i `operator=`.  
  
## <a name="example"></a>Przykład  
 Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) na przykład za pomocą `GetBSTR`.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_bstr_t, klasa](../cpp/bstr-t-class.md)