---
title: Błąd kompilatora C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: 321ccd23bc273f5fa548f75fd44bc320bcf4c426
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225517"
---
# <a name="compiler-error-c2384"></a>Błąd kompilatora C2384

"member": nie można zastosować __declspec (thread) do składowej klasy zarządzanej lub WinRT

Modyfikator [wątku](../../cpp/thread.md) **`__declspec`** nie może być używany w składowej klasy zarządzanej ani środowisko wykonawcze systemu Windows.

Lokalny magazyn wątków statycznych w kodzie zarządzanym może być używany tylko dla bibliotek DLL ładowanych statycznie — Biblioteka DLL musi być załadowana statycznie podczas uruchamiania procesu. Środowisko wykonawcze systemu Windows nie obsługuje lokalnego magazynu wątków.

Poniższy wiersz generuje C2384 i pokazuje, jak rozwiązać ten problem w kodzie C++/CLI:

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
