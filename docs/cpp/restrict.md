---
title: Ogranicz | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: restrict_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9176336ac96d88a34d758fd55c09a3a938f371fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="restrict"></a>ograniczenie
**Dotyczące firmy Microsoft**  
  
 Stosowane do deklaracji lub definicji funkcji zwracające typ wskaźnika i informuje kompilator, że funkcja zwraca obiekt, który nie będą używane z aliasem z innych wskaźników.  
  
## <a name="syntax"></a>Składnia  
  
```  
__declspec(restrict) return_type f();  
```  
  
## <a name="remarks"></a>Uwagi  
 Kompilator rozpropaguje `__declspec(restrict)`. Na przykład CRT `malloc` zostanie nadany funkcja `__declspec(restrict)` i w związku z tym zainicjować wskaźników do lokalizacji pamięci `malloc` są również niejawnego nie mieć aliasy.  
  
 Kompilator nie sprawdza, czy wskaźnik faktycznie nie jest używane z aliasem. Odpowiada dewelopera upewnij się, program nie alias jest oznaczony atrybutem wskaźnik `restrict __declspec` modyfikator.  
  
 Dla podobnych semantyki na zmiennych, zobacz [__restrict](../cpp/extension-restrict.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [noalias](../cpp/noalias.md) na przykład za pomocą `restrict`.  
  
 Aby uzyskać informacje o Ogranicz — słowo kluczowe, który jest częścią C++ AMP, zobacz [Ogranicz (C++ AMP)](../cpp/restrict-cpp-amp.md).  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)