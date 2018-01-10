---
title: Specyfikatory | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 352ef898c9380c55e90205129ba6fe48bf352856
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="specifiers"></a>Specyfikatory
W tym temacie opisano *specyfikatory decl* (specyfikatory deklaracji) składnik [deklaracji](declarations-and-definitions-cpp.md).  
  
 Następujące elementy zastępcze i słów kluczowych języka są specyfikatory deklaracji:  
  
 *Specyfikator klasy magazynu*  
  
 *Specyfikator typu*  
  
 *Specyfikator funkcji*  
  
 [Friend](../cpp/friend-cpp.md)  
  
 [Element TypeDef](http://msdn.microsoft.com/en-us/cc96cf26-ba93-4179-951e-695d1f5fdcf1)  
  
 [__declspec](../cpp/declspec.md) `(` *rozszerzony decl — modyfikator seq*`)`  
  
## <a name="remarks"></a>Uwagi  
 *Specyfikatory decl* najdłuższym sekwencji jest częścią deklaracji *specyfikatory decl* które można podjąć w celu oznacza nazwę typu, nie włączając wskaźnik lub odwołanie modyfikatorów. W pozostałej części deklaracji jest *deklarator*, w tym nazwa wprowadzona.  
  
 W poniższej tabeli przedstawiono cztery deklaracje i zawiera listę poszczególnych deklaracji *decl specifers* i *deklarator* składnika osobno.  
  
|Deklaracja|*Specyfikatory Decl*|`declarator`|  
|-----------------|------------------------|------------------|  
|`char *lpszAppName;`|`char`|`*lpszAppName`|  
|`typedef char * LPSTR;`|`char`|`*LPSTR`|  
|`const int func1();`|`const int`|`func1`|  
|`volatile void *pvvObj;`|`volatile void`|`*pvvObj`|  
  
 Ponieważ `signed`, `unsigned`, `long`, i `short` oznacza wszystkie `int`, `typedef` nazwę poniżej jedną z następujących słów kluczowych przyjmuje się członkiem *deklarator listy* nie pochodzi z *specyfikatory decl*.  
  
> [!NOTE]
>  Ponieważ nazwa może zostać ponownie zadeklarowana, interpretacji podlega najnowszych deklaracji w bieżącym zakresie. Ponowna deklaracja może mieć wpływ na sposób nazw będą interpretowane przez kompilator, szczególnie `typedef` nazwy.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje i definicje](declarations-and-definitions-cpp.md)