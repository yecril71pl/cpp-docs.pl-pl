---
title: Specyfikatory | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d437b70148fdaba4c8eb4d7aa855e7d75f6f2487
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953750"
---
# <a name="specifiers"></a>Specyfikatory
W tym temacie opisano *specyfikatorów decl* składnik (specyfikatory deklaracji) [deklaracji](declarations-and-definitions-cpp.md).  
  
 Następujące symbole zastępcze i słowa kluczowe języka są specyfikatory deklaracji:  
  
 *Specyfikator klasy magazynu*  
  
 *Specyfikator typu*  
  
 *Specyfikator funkcji*  
  
 [friend](../cpp/friend-cpp.md)  
  
 [typedef] ( [typedef](http://msdn.microsod) `(` *extended-decl modyfikator seq* `)`  
  
## <a name="remarks"></a>Uwagi  
 *Specyfikatorów decl* część deklaracji jest najdłuższym sekwencji *specyfikatorów decl* mogą być podejmowane oznacza nazwę typu, nie wliczając wskaźnika lub odwołania modyfikatorów. Pozostała część deklaracji jest *deklaratora*, które zawiea nazwę wprowadzone.  
  
 Poniższa tabela zawiera cztery deklaracje, a następnie każdego zgłoszenia *decl specifers* i *deklaratora* składnik oddzielnie.  
  
|Deklaracja|*specyfikatorów Decl*|`declarator`|  
|-----------------|------------------------|------------------|  
|`char *lpszAppName;`|**char**|`*lpszAppName`|  
|`typedef char * LPSTR;`|**char**|`*LPSTR`|  
|`const int func1();`|**Const int**|`func1`|  
|`volatile void *pvvObj;`|**volatile void**|`*pvvObj`|  
  
 Ponieważ **podpisany**, **niepodpisane**, **długie**, i **krótki** oznacza wszystkie **int**,  **Element TypeDef** nazwę jednego z tych słów kluczowych przyjmuje się członkiem następujących *lista deklaratorów* nie *specyfikatorów decl*.  
  
> [!NOTE]
>  Ponieważ może być ponownie zadeklarowany nazwa, interpretację podlega najnowszych deklaracji w bieżącym zakresie. Ponowna deklaracja może mieć wpływ na sposób nazwy będą interpretowane przez kompilator, szczególnie `typedef` nazwy.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje i definicje](declarations-and-definitions-cpp.md)