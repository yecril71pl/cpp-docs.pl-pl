---
title: '_variant_t:: oddziel | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::Detach
- _variant_t.Detach
dev_langs: C++
helpviewer_keywords:
- VARIANT object [C++], detatch
- Detach method [C++]
- VARIANT object
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 577b4874dd6d89c0c6c60b1a7981e74944e77ba8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="varianttdetach"></a>_variant_t::Detach
**Dotyczące firmy Microsoft**  
  
 Odłącza hermetyzowany **VARIANT** obiektu z tego `_variant_t` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
VARIANT Detach( );  
  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Hermetyzowany **VARIANT**.  
  
## <a name="remarks"></a>Uwagi  
 Wyodrębnia i zwraca hermetyzowany **VARIANT**, spowoduje to wyczyszczenie `_variant_t` obiektu bez niszczenia go. Usuwa funkcji członkowskiej **VARIANT** z hermetyzacji i zestawy **VARTYPE** tego `_variant_t` do obiektu `VT_EMPTY`. Należy zwolnić zwracana jest **VARIANT** przez wywołanie metody [VariantClear](http://msdn.microsoft.com/en-us/28741d81-8404-4f85-95d3-5c209ec13835) funkcji.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_variant_t, klasa](../cpp/variant-t-class.md)