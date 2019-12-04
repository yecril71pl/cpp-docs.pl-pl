---
title: Błąd kompilatora C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: 2ce5c2f2540fbd2aca3509fa1dac55073a002abb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745268"
---
# <a name="compiler-error-c2384"></a>Błąd kompilatora C2384

"member": nie można zastosować __declspec (thread) do składowej klasy zarządzanej lub WinRT

Nie można użyć modyfikatora `__declspec` [wątku](../../cpp/thread.md) dla elementu członkowskiego klasy zarządzanej lub środowisko wykonawcze systemu Windows.

Lokalny magazyn wątków statycznych w kodzie zarządzanym może być używany tylko dla bibliotek DLL ładowanych statycznie — Biblioteka DLL musi być załadowana statycznie podczas uruchamiania procesu. Środowisko wykonawcze systemu Windows nie obsługuje lokalnego magazynu wątków.

Poniższy wiersz generuje C2384 i pokazuje, jak rozwiązać ten problem w C++kodzie/CLI:

```cpp
// C2384.cpp
// compile with: /clr /c
public ref class B {
public:
   __declspec( thread ) static int tls_i = 1;   // C2384

   // OK - declare with attribute instead
   [System::ThreadStaticAttribute]
   static int tls_j;
};
```
