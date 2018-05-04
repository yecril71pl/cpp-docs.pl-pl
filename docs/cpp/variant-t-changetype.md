---
title: _variant_t::ChangeType | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53fd73fc9606053dda6f8c143618373ad9bb7e4e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType
**Microsoft Specific**  
  
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