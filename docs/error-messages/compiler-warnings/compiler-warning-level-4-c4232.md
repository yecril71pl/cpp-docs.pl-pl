---
title: Ostrzeżenie kompilatora (poziom 4) C4232
ms.date: 11/04/2016
f1_keywords:
- C4232
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
ms.openlocfilehash: c0e79dfa4564960a5660f0932b142b436370ac05
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173923"
---
# <a name="compiler-warning-level-4-c4232"></a>Ostrzeżenie kompilatora (poziom 4) C4232

użyto niestandardowego rozszerzenia: "Identyfikator": adres elementu dllimport "dllimport" nie jest statyczny, tożsamość nie jest gwarantowana

W obszarze rozszerzenia Microsoft (/ze) można nadać wartości niestatycznej jako adres funkcji zadeklarowanej za pomocą modyfikatora **dllimport** . W obszarze zgodność ze standardem ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) powoduje to wystąpienie błędu.

Poniższy przykład generuje C4232:

```c
// C4232.c
// compile with: /W4 /Ze /c
int __declspec(dllimport) f();
int (*pfunc)() = &f;   // C4232
```
