---
title: Ostrzeżenie kompilatora (poziom 4) C4295
ms.date: 01/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: 5e8b546e4eb4b60197db504382b3230e779b1dec
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924848"
---
# <a name="compiler-warning-level-4-c4295"></a>Ostrzeżenie kompilatora (poziom 4) C4295

> "*Array*": tablica jest zbyt mała, aby można było uwzględnić kończący znak null

Tablica została zainicjowana, ale ostatni znak w tablicy nie jest wartością null. Uzyskiwanie dostępu do tablicy jako ciągu może spowodować uzyskanie nieoczekiwanych wyników.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4295. Aby rozwiązać ten problem, można zadeklarować większy rozmiar tablicy w celu przechowywania kończącego się wartości null z ciągu inicjatora lub można użyć listy inicjatora tablicy, aby określić, że jest to tablica `char`, a nie ciąg zakończony znakiem null.

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
