---
title: Ostrzeżenie kompilatora (poziom 1) C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: 7d669280c0dc6a730a22480e602dac8cc6153449
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052380"
---
# <a name="compiler-warning-level-1-c4794"></a>Ostrzeżenie kompilatora (poziom 1) C4794

segment zmiennej lokalnego magazynu wątku "variable" został zmieniony z "Nazwa sekcji" na ". TLS $"

Użyto [#pragma data_seg](../../preprocessor/data-seg.md) , aby umieścić zmienną TLS w sekcji, która nie zaczyna się od. TLS $.

Sekcja. TLS $*x* będzie istnieć w pliku obiektu, w którym zdefiniowano zmienne [__declspec (wątku)](../../cpp/thread.md) . Sekcja. TLS w pliku EXE lub DLL będzie wynikać z tych sekcji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4794:

```cpp
// C4794.cpp
// compile with: /W1 /c
#pragma data_seg(".someseg")
__declspec(thread) int i;   // C4794

// OK
#pragma data_seg(".tls$9")
__declspec(thread) int j;
```