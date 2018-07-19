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
ms.openlocfilehash: f87d9e4d7193755f70e3463f4da60d88a7bd832c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947845"
---
# <a name="varianttchangetype"></a>_variant_t::ChangeType
**Microsoft Specific**  
  
 Zmienia typ `_variant_t` wskazany obiekt `VARTYPE`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
void ChangeType(  
   VARTYPE vartype,  
   const _variant_t* pSrc = NULL   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *VarType*  
 `VARTYPE` Tego `_variant_t` obiektu.  
  
 *pSrc*  
 Wskaźnik do `_variant_t` obiekt do skonwertowania. Jeśli ta wartość wynosi NULL, konwersja odbywa się w miejscu.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja elementu członkowskiego konwertuje `_variant_t` wskazany obiekt `VARTYPE`. Jeśli *pSrc* ma wartość NULL, konwersja odbywa się w miejscu, w przeciwnym razie to `_variant_t` obiekt jest kopiowany z *pSrc* , a następnie konwertowana.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_variant_t, klasa](../cpp/variant-t-class.md)