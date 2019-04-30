---
title: Kompilator ostrzeżenie (poziom 4) C4295
ms.date: 1/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: ed31ea19f9c36a9c6fab7452a4bfc3843a151059
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400880"
---
# <a name="compiler-warning-level-4-c4295"></a>Kompilator ostrzeżenie (poziom 4) C4295

> "*tablicy*": tablica jest zbyt mała, aby uwzględnić znak końcowy null

Tablica został zainicjowany, ale ostatni znak w tablicy nie ma wartość null; Uzyskiwanie dostępu do tablicy jako ciąg może dać nieoczekiwane wyniki.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4295. Aby rozwiązać ten problem, można zadeklarować rozmiar tablicy większe, aby pomieścić zakończenia o wartości null z ciągu inicjatora lub możesz użyć listy inicjatora tablicy się wyczyść intencji, że jest to tablica `char`, nie ciąg zakończony znakiem null.

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
