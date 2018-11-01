---
title: Błąd kompilatora C2384
ms.date: 11/04/2016
f1_keywords:
- C2384
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
ms.openlocfilehash: 1909fb999dd0f60224029b726f773c11fa69ee40
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460323"
---
# <a name="compiler-error-c2384"></a>Błąd kompilatora C2384

'składowa': nie można zastosować __declspec(thread) do członkiem zarządzanej lub klasa WinRT

[Wątku](../../cpp/thread.md) `__declspec` modyfikatora nie można używać na członkiem zarządzanej lub klasy środowiska wykonawczego Windows.

Statyczne wątku Magazyn lokalny w kodzie zarządzanym można używać tylko dla statycznie ładowanych bibliotek DLL — biblioteki DLL muszą być statycznie ładowane podczas uruchamiania procesu. Środowisko uruchomieniowe Windows nie obsługuje pamięci lokalnej wątku.

Następujące polecenie generuje C2384 i pokazuje, jak go naprawić w języku C + +/ CLI, kod:

```
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