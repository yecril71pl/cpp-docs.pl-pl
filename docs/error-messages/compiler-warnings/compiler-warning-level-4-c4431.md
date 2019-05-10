---
title: Kompilator ostrzeżenie (poziom 4) C4431
ms.date: 11/04/2016
f1_keywords:
- C4431
helpviewer_keywords:
- C4431
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
ms.openlocfilehash: 6a07a9ffa938d9372ebed9676847b3274115d526
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447020"
---
# <a name="compiler-warning-level-4-c4431"></a>Kompilator ostrzeżenie (poziom 4) C4431

brak specyfikatora typu — zakładany int. Uwaga: C nie obsługuje już domyślnie typu int

Ten błąd można wygenerować w wyniku pracy zgodności kompilatora, która została wykonana dla programu Visual Studio 2005: Wizualne C++ jako domyślnie nie jest już tworzy identyfikatory bez typu. Typ identyfikatora musi być jawnie określone.

To ostrzeżenie jest domyślnie wyłączona. Zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4431.

```
// C4431.c
// compile with: /c /W4
#pragma warning(default:4431)
i;   // C4431
int i;   // OK
```