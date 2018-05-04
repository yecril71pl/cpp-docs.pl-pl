---
title: _variant_t::Dołącz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::Attach
- _variant_t.Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method [C++]
- VARIANT object [C++], attach
- VARIANT object
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93c4ec0b4d25f1ca0ec03d9aae1dd9e1c16b79a9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="varianttattach"></a>_variant_t::Attach
**Microsoft Specific**  
  
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