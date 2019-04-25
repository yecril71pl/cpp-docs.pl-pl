---
title: Specyfikatory
ms.date: 11/04/2016
helpviewer_keywords:
- declaration specifiers
- declarations, specifiers
- specifiers, in declarations
ms.assetid: 8b14e844-9880-4571-8779-28c8efe44633
ms.openlocfilehash: aef967b26321f289cb8c7bd0402d7fe8f12b77b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330989"
---
# <a name="specifiers"></a>Specyfikatory

W tym temacie opisano *specyfikatorów decl* składnik (specyfikatory deklaracji) [deklaracji](declarations-and-definitions-cpp.md).

Następujące symbole zastępcze i słowa kluczowe języka są specyfikatory deklaracji:

*storage-class-specifier*

*type-specifier*

*Specyfikator funkcji*

[friend](friend-cpp.md)

[typedef](aliases-and-typedefs-cpp.md) `(` *extended-decl-modifier-seq* `)`

[__declspec](declspec.md) `(` *extended-decl-modifier-seq* `)`

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
