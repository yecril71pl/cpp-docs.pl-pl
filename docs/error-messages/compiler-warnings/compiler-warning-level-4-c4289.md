---
title: Ostrzeżenie kompilatora (poziom 4) C4289
ms.date: 11/04/2016
f1_keywords:
- C4289
helpviewer_keywords:
- C4289
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
ms.openlocfilehash: cc1a22065be6d5f7f49d6c32f6bc9b6479399e29
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541974"
---
# <a name="compiler-warning-level-4-c4289"></a>Ostrzeżenie kompilatora (poziom 4) C4289

użyte rozszerzenie niestandardowe: 'var' : zmienna sterowania pętlą zadeklarowana w pętli for jest używana poza zakresem pętli for

Podczas kompilowania z [/ze](../../build/reference/za-ze-disable-language-extensions.md) i **/Zc: forScope-** , zmienna zadeklarowana w pętli [for](../../cpp/for-statement-cpp.md) została użyta po zakresie pętli **for**.

Zobacz [/Zc: forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) , aby uzyskać informacje na temat sposobu określania zachowania standardowego w programie **dla** pętli z **/ze**.

To ostrzeżenie jest domyślnie wyłączone. Aby uzyskać więcej informacji [, zobacz ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Poniższy przykład generuje C4289:

```cpp
// C4289.cpp
// compile with: /W4 /Zc:forScope-
#pragma warning(default:4289)
int main() {
   for (int i = 0 ; ; )   // C4289
      break;
   i++;
}
```