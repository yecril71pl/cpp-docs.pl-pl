---
title: "_variant_t — operatory relacyjne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _variant_t::operator==
- _variant_t::operator!=
dev_langs: C++
helpviewer_keywords:
- '!= operator'
- relational operators [C++], _variant_t class
- operator!= [C++], variant
- operator!= [C++], relational operators
- operator != [C++], variant
- operator == [C++], variant
- operator== [C++], variant
- operator != [C++], relational operators
- == operator [C++], with specific Visual C++ objects
ms.assetid: 141bacb8-41a2-44dd-b3c0-4ad1f884f4ea
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eacfe9584cedfd45a952dca62dae545f617b1433
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="variantt-relational-operators"></a>_variant_t — Operatory relacyjne
**Dotyczące firmy Microsoft**  
  
 Porównać dwa `_variant_t` obiektów równości i nierówności.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      bool operator==(  
   const VARIANT& varSrc   
) const;  
bool operator==(  
   const VARIANT* pSrc   
) const;  
bool operator!=(  
   const VARIANT& varSrc   
) const;  
bool operator!=(  
   const VARIANT* pSrc   
) const;  
```  
  
#### <a name="parameters"></a>Parametry  
 *varSrc*  
 A **VARIANT** ma zostać porównane z `_variant_t` obiektu.  
  
 `pSrc`  
 Wskaźnik do **VARIANT** ma zostać porównane z `_variant_t` obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli przechowuje porównania, **false** , jeśli nie.  
  
## <a name="remarks"></a>Uwagi  
 Porównuje `_variant_t` obiekt z **VARIANT**, testowanie równości i nierówności.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [_variant_t — klasa](../cpp/variant-t-class.md)