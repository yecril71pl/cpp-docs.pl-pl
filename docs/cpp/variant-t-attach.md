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
ms.openlocfilehash: 42c275d085434cc8077a0629429c7c0e1cbbfcc3
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947935"
---
# <a name="varianttattach"></a>_variant_t::Attach
**Microsoft Specific**  
  
 Dołącza `VARIANT` do obiektu `_variant_t` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
void Attach(VARIANT& varSrc);  
```  
  
#### <a name="parameters"></a>Parametry  
 *varSrc*  
 A `VARIANT` obiekt dołączony do tego `_variant_t` obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Przejmuje na własność `VARIANT` poprzez hermetyzację go. Ta funkcja elementu członkowskiego zwalnia wszystkie istniejące hermetyzowane `VARIANT`, następnie kopiuje podane `VARIANT`i ustawia jego `VARTYPE` do VT_EMPTY, aby upewnić się, że można zwolnić tylko jej zasoby, `_variant_t` destruktora.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_variant_t, klasa](../cpp/variant-t-class.md)