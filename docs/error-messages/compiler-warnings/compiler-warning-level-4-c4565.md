---
title: Kompilator ostrzeżenie (poziom 4) C4565
ms.date: 08/27/2018
f1_keywords:
- C4565
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
ms.openlocfilehash: b655dcfb456d32e45833e89e5a48926ad70d1d9e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220484"
---
# <a name="compiler-warning-level-4-c4565"></a>Kompilator ostrzeżenie (poziom 4) C4565

> "*funkcja*": zmiana definicji; symbol został poprzednio zadeklarowany za pomocą __declspec (*modyfikator*)

## <a name="remarks"></a>Uwagi

Symbol został ponownie zdefiniować lub ponownie zadeklarowany, a drugi definicji lub deklaracji, w odróżnieniu od pierwszej definicji lub deklaracji, nie ma `__declspec` modyfikator (*modyfikator*). To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, usuń jedną z definicji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4565:

```cpp
// C4565.cpp
// compile with: /W4 /LD
__declspec(noalias) void f();
void f();   // C4565
```