---
title: "ctype_base — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: locale/std::ctype_base
dev_langs: C++
helpviewer_keywords: ctype_base class
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 83f467f8d06956678795bf97fed60fe9f22c32f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ctypebase-class"></a>ctype_base — Klasa
Klasa służy jako klasę podstawową dla aspekty szablonu klasy [ctype](../standard-library/ctype-class.md). Klasa bazowa dla klasy ctype, która jest używana do definiowania typów wyliczeń używanych w celu klasyfikowania lub testowania znaków indywidualnie lub w ramach całych zakresów.  
  
## <a name="syntax"></a>Składnia  
  
```
struct ctype_base : public locale::facet
{
    enum
 {
    alnum,
 alpha,
    cntrl,
 digit,
    graph,
 lower,
    print,
 punct,
    space,
 upper,
    xdigit
 };
    typedef short mask;
    ctype_base(
 size_t _Refs = 0);

 ~ctype_base();

};
```  
  
## <a name="remarks"></a>Uwagi  
 Definiuje wyliczenie maski. Każdy stała wyliczenia charakteryzuje sposobu klasyfikowania znaków, zgodnie z definicją przez funkcje o podobnej nazwie zadeklarowany w nagłówku \<ctype.h >. Stałe są:  
  
- **miejsce** (funkcja [isspace —](../standard-library/locale-functions.md#isspace))  
  
- **Drukowanie** (funkcja [isprint —](../standard-library/locale-functions.md#isprint))  
  
- **nacisnąć klawisze CTRL +** (funkcja [iscntrl —](../standard-library/locale-functions.md#iscntrl))  
  
- **Górny** (funkcja [isupper —](../standard-library/locale-functions.md#isupper))  
  
- **niższe** (funkcja [islower —](../standard-library/locale-functions.md#islower))  
  
- **cyfra** (funkcja [isdigit —](../standard-library/locale-functions.md#isdigit))  
  
- **punct** (funkcja [ispunct —](../standard-library/locale-functions.md#ispunct))  
  
- **xdigit** (funkcja [isxdigit —](../standard-library/locale-functions.md#isxdigit))  
  
- **Alpha** (funkcja [isalpha —](../standard-library/locale-functions.md#isalpha))  
  
- **alnum** (funkcja [isalnum —](../standard-library/locale-functions.md#isalnum))  
  
- **Wykres** (funkcja [isgraph —](../standard-library/locale-functions.md#isgraph))  
  
 Kombinację klasyfikacje przez ORing można określić te stałe. W szczególności jest zawsze wartość true, który **alnum** == ( **alfa** &#124; **cyfrę** \) i **wykres** \= \= \( **alnum** &#124; **punct**).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



