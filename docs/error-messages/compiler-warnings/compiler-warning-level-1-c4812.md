---
title: Ostrzeżenie kompilatora (poziom 1) C4812
ms.date: 11/04/2016
f1_keywords:
- C4812
helpviewer_keywords:
- C4812
ms.assetid: a7f5721f-2019-44de-ad62-ed30bac8b1f3
ms.openlocfilehash: 9355886c3ec19e75cc1aa62f8cc41bba9f951d7c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174911"
---
# <a name="compiler-warning-level-1-c4812"></a>Ostrzeżenie kompilatora (poziom 1) C4812

przestarzała deklaracja stylu: zamiast niej użyj "new_syntax"

W bieżącej wersji wizualizacji C++Jawna specjalizacja konstruktora jest nadal obsługiwana, ale może nie być obsługiwana w przyszłych wydaniach.

Poniższy przykład generuje C4812:

```cpp
// C4812.cpp
// compile with: /W1 /c
template <class T>
class MyClass;

template<class T>
class MyClass<T*> {
   MyClass();
};

template<class T>
MyClass<T*>::MyClass<T*>() {}   // C4812
// try the following line instead
// MyClass<T*>::MyClass() {}
```
