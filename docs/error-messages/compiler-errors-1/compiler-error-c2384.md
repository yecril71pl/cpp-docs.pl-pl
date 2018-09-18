---
title: Błąd kompilatora C2384 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2384
dev_langs:
- C++
helpviewer_keywords:
- C2384
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3aa9ec8a6a94f53123c443a1149df7cdbc95c83
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020462"
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