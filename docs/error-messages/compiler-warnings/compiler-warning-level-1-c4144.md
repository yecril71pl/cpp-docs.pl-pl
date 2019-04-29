---
title: Kompilator ostrzeżenie (poziom 1) C4144
ms.date: 11/04/2016
f1_keywords:
- C4144
helpviewer_keywords:
- C4144
ms.assetid: a37b445d-dbc6-43b4-8d95-ffd0e4225464
ms.openlocfilehash: b2406357baf70e45566f2d2f25839d151bac4186
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352952"
---
# <a name="compiler-warning-level-1-c4144"></a>Kompilator ostrzeżenie (poziom 1) C4144

"expression": wyrażenie relacyjne jako wyrażenie przełącznik

Użyto określone wyrażenie relacyjne jako wyrażenie kontroli [Przełącz](../../cpp/switch-statement-cpp.md) instrukcji. Skojarzone instrukcji case oferowane są wartościami logicznymi. Poniższy przykład spowoduje wygenerowanie C4144:

```
// C4144.cpp
// compile with: /W1
int main()
{
   int i = 0;
   switch(!i) {   // C4144, remove the ! to resolve
      case 1:
         break;
      default:
         break;
   }
}
```