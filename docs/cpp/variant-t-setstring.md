---
title: _variant_t::SetString | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _variant_t::SetString
dev_langs:
- C++
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 090fd7ed027738ebe7bc9276e3b3f124b9212c4a
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463470"
---
# <a name="varianttsetstring"></a>_variant_t::SetString
**Microsoft Specific**  
  
 Przypisuje ten ciąg `_variant_t` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
void SetString(const char* pSrc);  
```  
  
#### <a name="parameters"></a>Parametry  
 *pSrc*  
 Wskaźnik do ciągu znaków.  
  
## <a name="remarks"></a>Uwagi  
 Konwertuje ciąg znaków ANSI Unicode `BSTR` ciąg, a następnie przypisuje go do tego `_variant_t` obiektu.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [_variant_t, klasa](../cpp/variant-t-class.md)