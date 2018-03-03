---
title: _bstr_t::GetAddress | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _bstr_t::GetAddress
dev_langs:
- C++
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c1b2b348277f7d33a32c8d0e6ad1fc80d51ec68d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress
**Dotyczące firmy Microsoft**  
  
 Zwalnia wszelkie istniejące parametry i zwraca adres nowoprzydzielonych ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
BSTR* GetAddress( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `BSTR` opakowane przez `_bstr_t`.  
  
## <a name="remarks"></a>Uwagi  
 `GetAddress`dotyczy wszystkich `_bstr_t` obiekty tego udziału `BSTR`. Więcej niż jeden `_bstr_t` mogą udostępniać `BSTR` przy użyciu konstruktora kopiującego i i `operator=`.  
  
## <a name="example"></a>Przykład  
 Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) na przykład użycie `GetAddress`.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_bstr_t, klasa](../cpp/bstr-t-class.md)