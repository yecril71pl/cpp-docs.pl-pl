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
ms.openlocfilehash: 8c1fb739d5e6206297e52fd9103cbba98c5eef01
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42464667"
---
# <a name="specifiers"></a>Specyfikatory
W tym temacie opisano *specyfikatorów decl* składnik (specyfikatory deklaracji) [deklaracji](declarations-and-definitions-cpp.md).  
  
 Następujące symbole zastępcze i słowa kluczowe języka są specyfikatory deklaracji:  
  
 *Specyfikator klasy magazynu*  
  
 *Specyfikator typu*  
  
 *Specyfikator funkcji*  
  
 [friend](friend-cpp.md)  
 
 [Element TypeDef](aliases-and-typedefs-cpp.md) `(` *extended-decl modyfikator seq* `)`  

 [__declspec](declspec.md) `(` *extended-decl modyfikator seq* `)`  
  
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
>  Ponieważ może być ponownie zadeklarowany nazwa, interpretację podlega najnowszych deklaracji w bieżącym zakresie. Ponowna deklaracja może mieć wpływ na sposób nazwy będą interpretowane przez kompilator, szczególnie **typedef** nazwy.  
  
## <a name="see-also"></a>Zobacz także  
 [Deklaracje i definicje](declarations-and-definitions-cpp.md)
