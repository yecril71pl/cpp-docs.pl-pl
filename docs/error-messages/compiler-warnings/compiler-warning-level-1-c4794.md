---
title: Ostrzeżenie kompilatora (poziom 1) C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: 7f7ea7555937069caf5f83c9bf00f0fa980ef020
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175119"
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
