---
title: _variant_t::ChangeType | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::ChangeType
- _variant_t.ChangeType
dev_langs:
- C++
helpviewer_keywords:
- ChangeType method [C++]
- VARIANT object [C++], ChangeType
- VARIANT object
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fb59090ebc4c6ff9120e813ae12a9defbe618b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType
**Dotyczące firmy Microsoft**  
  
 Zmienia typ `_variant_t` wskazany obiekt **VARTYPE**.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      void ChangeType(  
   VARTYPE vartype,  
   const _variant_t* pSrc = NULL   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `vartype`  
 **VARTYPE** dla tego `_variant_t` obiektu.  
  
 `pSrc`  
 Wskaźnik do `_variant_t` obiektu do skonwertowania. Jeśli ta wartość jest **NULL**, konwersja odbywa się w miejscu.  
  
## <a name="remarks"></a>Uwagi  
 Konwertuje funkcji członkowskiej `_variant_t` wskazany obiekt **VARTYPE**. Jeśli `pSrc` jest **NULL**, konwersja odbywa się w miejscu, w przeciwnym razie to `_variant_t` obiektu zostaną skopiowane z `pSrc` , a następnie konwertowana.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_variant_t, klasa](../cpp/variant-t-class.md)