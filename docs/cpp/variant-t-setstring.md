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
ms.openlocfilehash: 68ef72cfd256a2676c73223723f37374c50cb56f
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947872"
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
  
## <a name="see-also"></a>Zobacz też  
 [_variant_t, klasa](../cpp/variant-t-class.md)