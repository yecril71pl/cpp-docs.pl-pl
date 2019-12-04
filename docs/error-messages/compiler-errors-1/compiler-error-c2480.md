---
title: Błąd kompilatora C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 3e495a8019405a558511637467133877dae1183e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743526"
---
# <a name="compiler-error-c2480"></a>Błąd kompilatora C2480

"Identyfikator": "Thread" jest tylko prawidłowy dla elementów danych statycznego zakresu

Nie można użyć atrybutu `thread` ze zmienną automatyczną, niestatyczną składową danych, parametrem funkcji ani deklaracjami lub definicjami funkcji.

Użyj atrybutu `thread` dla zmiennych globalnych, statycznych elementów członkowskich danych i lokalnych zmiennych statycznych.

Poniższy przykład generuje C2480:

```cpp
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```
