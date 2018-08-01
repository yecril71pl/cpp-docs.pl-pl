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
ms.openlocfilehash: f28ae7b7cb8bdcf335757c58d5e744974f4c7cad
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39405960"
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
  
## <a name="see-also"></a>Zobacz także  
 [Keywords](../cpp/keywords-cpp.md)   
 [override, specyfikator](../cpp/override-specifier.md)