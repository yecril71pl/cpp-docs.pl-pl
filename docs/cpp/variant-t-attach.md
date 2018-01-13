---
title: "_variant_t::Dołącz | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs: C++
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: effeaaaf3f8df9eb100d5e92e760eb439a865552
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="varianttattach"></a>_variant_t::Attach
**Dotyczące firmy Microsoft**  
  
 Dołącza **VARIANT** obiekt do `_variant_t` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      void Attach(  
   VARIANT& varSrc   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *varSrc*  
 A **VARIANT** obiektu jest dołączony do tego `_variant_t` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Przejście własności **VARIANT** hermetyzując go. Funkcji członkowskiej zwalnia wszystkie istniejące hermetyzowany **VARIANT**, następnie kopiuje podane **VARIANT**i ustawia jego **VARTYPE** do `VT_EMPTY` do upewnij się, że jego Zasoby można zwolnić tylko przez `_variant_t` destruktora.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_variant_t, klasa](../cpp/variant-t-class.md)