---
title: Ostrzeżenie kompilatora (poziom 1) C4085
ms.date: 11/04/2016
f1_keywords:
- C4085
helpviewer_keywords:
- C4085
ms.assetid: 2bc6eb25-058f-4597-b351-fd69587b5170
ms.openlocfilehash: 8fc8ddc900299f372f0592b660b132188128c3d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200203"
---
# <a name="compiler-warning-level-1-c4085"></a>Ostrzeżenie kompilatora (poziom 1) C4085

Oczekiwano parametru pragma "on" lub "off"

Dyrektywa pragma wymaga parametru **on** lub **off** . Pragma jest ignorowana.

Poniższy przykład generuje C4085:

```cpp
// C4085.cpp
// compile with: /W1 /LD
#pragma optimize( "t", maybe )  // C4085
```
