---
title: Kompilator ostrzeżenie (poziom 4) C4366
ms.date: 11/04/2016
f1_keywords:
- C4366
helpviewer_keywords:
- C4366
ms.assetid: 65d2942f-3741-42f4-adf2-4920d5a055ca
ms.openlocfilehash: 11fcb0070359201de39ca5f33c83d000e02f0835
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391559"
---
# <a name="compiler-warning-level-4-c4366"></a>Kompilator ostrzeżenie (poziom 4) C4366

Wynik operatora jednoargumentowego "operator" może być niewyrównany

Jeśli element członkowski struktury nigdy nie może być niewyrównany spowodowane pakowania, kompilator wyświetli ostrzeżenie, gdy czy adres elementu członkowskiego jest przypisany do wskaźnika wyrównane. Domyślnie wszystkie wskaźniki są wyrównane.

Aby rozwiązać C4366, Zmień wyrównanie struktury lub zadeklarować wskaźnika za pomocą [__unaligned](../../cpp/unaligned.md) — słowo kluczowe.

Aby uzyskać więcej informacji, zobacz __unaligned i [pakiet](../../preprocessor/pack.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4366.

```
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