---
title: Ostrzeżenie kompilatora (poziom 4) C4366
ms.date: 11/04/2016
f1_keywords:
- C4366
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
ms.openlocfilehash: 18045377210b6c020786ad2ec2e003d0e764e4b5
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683262"
---
# <a name="compiler-warning-level-4-c4366"></a>Ostrzeżenie kompilatora (poziom 4) C4366

Wynik operatora jednoargumentowego "operator" może być niewyrównany

Jeśli element członkowski struktury może być niewyrównany z powodu pakowania, kompilator wyświetli ostrzeżenie, gdy adres tego elementu członkowskiego zostanie przypisany do wyrównanego wskaźnika. Domyślnie wszystkie wskaźniki są wyrównane.

Aby rozwiązać C4366, Zmień wyrównanie struktury lub Zadeklaruj wskaźnik za pomocą słowa kluczowego [__unaligned](../../cpp/unaligned.md) .

Aby uzyskać więcej informacji, zobacz __unaligned i [Pack](../../preprocessor/pack.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4366.

```cpp
// C4366.cpp
// compile with: /W4 /c
// processor: IPF x64
#pragma pack(1)
struct X {
   short s1;
   int s2;
};

int main() {
   X x;
   short * ps1 = &x.s1;   // OK
   int * ps2 = &x.s2;   // C4366
}
```