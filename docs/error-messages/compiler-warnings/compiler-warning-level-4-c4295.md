---
title: Kompilator ostrzeżenie (poziom 4) C4295 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 1/09/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4295
dev_langs:
- C++
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36c6ac4d8c3e2899b744d1c456ae3079ec031698
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053586"
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
