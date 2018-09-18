---
title: Błąd kompilatora C3269 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3269
dev_langs:
- C++
helpviewer_keywords:
- C3269
ms.assetid: c575f067-244d-4dd5-bf58-9e7630ea58b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 84cb9acdd6444b934e7ec51691d87a6912880de2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061815"
---
# <a name="compiler-error-c3269"></a>Błąd kompilatora C3269

'Funkcja': nie można zadeklarować funkcji składowej typu zarządzanego lub WinRTtype przy użyciu "..."

Funkcje składowych klasy WinRT nie może deklarować parametrów o zmiennej długości, list i zarządzane.

Poniższy przykład generuje C3269 i pokazuje, jak go naprawić:

```
// C3269_2.cpp
// compile with: /clr

ref struct A
{
   void func(int i, ...)   // C3269
   // try the following line instead
   // void func(int i )
   {
   }
};

int main()
{
}
```
