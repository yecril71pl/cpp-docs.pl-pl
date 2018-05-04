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
ms.openlocfilehash: 82fb9e13fc5dbbafcc37905716a37322b2966c6d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="final-specifier"></a>final, specyfikator
Można użyć `final` — słowo kluczowe do wyznaczenia wirtualnego funkcje, których nie można zastąpić w klasie pochodnej. Można również użyć do wyznaczenia klasy, które nie może być dziedziczona.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
function-declaration final;  
```  
  
```  
  
class class-name final base-classes  
```  
  
## <a name="remarks"></a>Uwagi  
 `final` kontekstowa i ma specjalne znaczenie tylko wtedy, gdy jest używany po deklaracji funkcji lub nazwy klasy; w przeciwnym razie nie jest zarezerwowanym słowem kluczowym.  
  
 Gdy `final` jest używany w deklaracjach klas `base-classes` jest opcjonalnym składnikiem deklaracji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `final` — słowo kluczowe, aby określić, czy funkcji wirtualnej nie można zastąpić.  
  
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
  
 Informacje o sposobie określania funkcje Członkowskie mogą zostać zastąpione, zobacz [specyfikator przesłonięcia](../cpp/override-specifier.md).  
  
 W następnym przykładzie użyto `final` — słowo kluczowe, aby określić, że klasa nie może być dziedziczona.  
  
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