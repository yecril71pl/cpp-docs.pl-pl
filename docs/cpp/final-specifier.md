---
title: final, Specyfikator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- final_CPP
dev_langs:
- C++
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 594bc432cb12b63c76172b06ee078d5b0f72de55
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947747"
---
# <a name="final-specifier"></a>final, specyfikator
Możesz użyć **końcowego** — słowo kluczowe, aby wyznaczyć funkcje wirtualne, które nie mogą być zastępowane w klasie pochodnej. Można również użyć do wyznaczenia klas, które nie może być dziedziczona.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
function-declaration final;  
class class-name final base-classes  
```  
  
## <a name="remarks"></a>Uwagi  
 **końcowe** jest zależny od kontekstu i ma specjalne znaczenie, gdy jest używany po deklarację funkcji lub klasy nazwę; w przeciwnym razie, nie jest zarezerwowanym słowem kluczowym tylko.  
  
 Gdy **końcowego** jest używany w deklaracjach klas `base-classes` jest opcjonalnym składnikiem deklaracji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto **końcowego** — słowo kluczowe, aby określić, czy funkcja wirtualna nie może być zastąpiona.  
  
```cpp  
class BaseClass  
{  
    virtual void func() final;  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void func(); // compiler error: attempting to   
                         // override a final function  
};  
```  
  
 Uzyskać informacji o sposobie określania, funkcje składowe można przesłonić, zobacz [specyfikator override](../cpp/override-specifier.md).  
  
 W następnym przykładzie użyto **końcowego** — słowo kluczowe, aby określić, że klasa nie może być dziedziczona.  
  
```cpp  
class BaseClass final   
{  
};  
  
class DerivedClass: public BaseClass // compiler error: BaseClass is   
                                     // marked as non-inheritable  
{  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Keywords](../cpp/keywords-cpp.md)   
 [override, specyfikator](../cpp/override-specifier.md)