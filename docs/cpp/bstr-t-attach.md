---
title: "_bstr_t::Dołącz | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _bstr_t::Attach
dev_langs: C++
helpviewer_keywords: Attach method [C++]
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0c6d60347b9b5be10923e23e839d99ddd0f1cee4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="bstrtattach"></a>_bstr_t::Attach
**Dotyczące firmy Microsoft**  
  
 Łącza `_bstr_t` otoki do `BSTR`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      void Attach(  
   BSTR s  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *s*  
 A `BSTR` skojarzone z lub przypisane do, `_bstr_t` zmiennej.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `_bstr_t` wcześniej był dołączony do innego `BSTR`, `_bstr_t` spowoduje oczyszczenie `BSTR` zasobu, jeśli żaden inny `_bstr_t` używania zmiennych `BSTR`.  
  
## <a name="example"></a>Przykład  
 Zobacz [_bstr_t::przypisanie](../cpp/bstr-t-assign.md) na przykład za pomocą **Attach**.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_bstr_t, klasa](../cpp/bstr-t-class.md)