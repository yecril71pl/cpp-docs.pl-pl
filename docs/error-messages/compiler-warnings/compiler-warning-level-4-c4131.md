---
title: Ostrzeżenie kompilatora (poziom 4) C4131
ms.date: 11/04/2016
f1_keywords:
- C4131
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
ms.openlocfilehash: 995891cc3b8391e09aea21751354abb189d7c8dd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198448"
---
# <a name="compiler-warning-level-4-c4131"></a>Ostrzeżenie kompilatora (poziom 4) C4131

"Function": używa deklarator starego stylu

Określona deklaracja funkcji nie jest w postaci prototypowej.

Deklaracje funkcji starego stylu powinny być konwertowane na formę prototypu.

W poniższym przykładzie pokazano deklarację funkcji starego stylu:

```c
// C4131.c
// compile with: /W4 /c
void addrec( name, id ) // C4131 expected
char *name;
int id;
{ }
```

Poniższy przykład przedstawia formę prototypu:

```c
void addrec( char *name, int id )
{ }
```
