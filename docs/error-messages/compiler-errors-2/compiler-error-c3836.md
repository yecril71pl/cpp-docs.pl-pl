---
title: Błąd kompilatora C3836
ms.date: 11/04/2016
f1_keywords:
- C3836
helpviewer_keywords:
- C3836
ms.assetid: 254f851b-7b7d-4c34-a740-fcf72f6a636a
ms.openlocfilehash: 9c8a7e761f2ece046d5de5c0e74ee911e5ee550d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741407"
---
# <a name="compiler-error-c3836"></a>Błąd kompilatora C3836

Konstruktor statyczny nie może mieć listy inicjatorów składowych

Klasa zarządzana nie może mieć konstruktora statycznego, który ma także listę inicjalizacji składowej. Konstruktory klas statycznych są wywoływane przez środowisko uruchomieniowe języka wspólnego do inicjowania klasy, inicjując statyczne składowe danych.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3836:

```cpp
// C3836a.cpp
// compile with: /clr
ref class M
{
   static int s_i;

public:
   static M() :  s_i(1234)   // C3836, delete initializer to resolve
   {
   }
};

int main()
{
}
```
