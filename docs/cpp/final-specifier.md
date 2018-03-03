---
title: final, Specyfikator | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- final_CPP
dev_langs:
- C++
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3f7c5afd4010983ea943193b7abfb99f22eda38
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
 `final`kontekstowa i ma specjalne znaczenie tylko wtedy, gdy jest używany po deklaracji funkcji lub nazwy klasy; w przeciwnym razie nie jest zarezerwowanym słowem kluczowym.  
  
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
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [override, specyfikator](../cpp/override-specifier.md)