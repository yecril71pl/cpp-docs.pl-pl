---
title: Ostrzeżenie kompilatora (poziom 3) C4619
ms.date: 11/04/2016
f1_keywords:
- C4619
helpviewer_keywords:
- C4619
ms.assetid: 701fea21-01aa-4bea-93d4-1cb8824170b0
ms.openlocfilehash: 658e52a2349f070def1efb80ca8a1cd93abca0cd
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991964"
---
# <a name="compiler-warning-level-3-c4619"></a>Ostrzeżenie kompilatora (poziom 3) C4619

Ostrzeżenie \#pragma: nie istnieje ostrzeżenie o numerze "number"

Podjęto próbę wyłączenia ostrzeżenia, które nie istnieje.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Poniższy przykład generuje C4619:

```cpp
// C4619.cpp
// compile with: /W3 /c
#pragma warning(default : 4619)
#pragma warning(disable : 4354)   // C4619, C4354 does not exist
```
