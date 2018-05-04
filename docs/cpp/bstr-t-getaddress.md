---
title: _bstr_t::GetAddress | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetAddress
dev_langs:
- C++
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88accb8b614a5a07a7abf688790a80786f465607
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress
**Microsoft Specific**  
  
 Zwalnia wszelkie istniejące parametry i zwraca adres nowoprzydzielonych ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
BSTR* GetAddress( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `BSTR` opakowane przez `_bstr_t`.  
  
## <a name="remarks"></a>Uwagi  
 `GetAddress` dotyczy wszystkich `_bstr_t` obiekty tego udziału `BSTR`. Więcej niż jeden `_bstr_t` mogą udostępniać `BSTR` przy użyciu konstruktora kopiującego i i `operator=`.  
  
## <a name="example"></a>Przykład  
 Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) na przykład użycie `GetAddress`.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_bstr_t, klasa](../cpp/bstr-t-class.md)