---
title: Kompilatora (poziom 4) ostrzeżenie C4295 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 815a669bc359121b13b1d636009cad81dc332304
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296305"
---
# <a name="compiler-warning-level-4-c4295"></a>Kompilator C4295 ostrzegawcze (poziom 4)
  
> "*tablicy*": tablica jest zbyt mała, aby uwzględnić znak końcowy null  
  
Tablica został zainicjowany, ale ostatni znak w tablicy nie jest wartość null; Uzyskiwanie dostępu do tablicy jako ciąg może dać nieoczekiwane wyniki.  
  
## <a name="example"></a>Przykład  
  
Poniższy przykład generuje C4295. Aby rozwiązać ten problem, można deklarowaniu rozmiar tablicy większy, aby pomieścić zakończenia null z ciągu inicjatora, lub można użyć listy inicjatora tablicy można dokonać konwersji wyczyść zaznaczenie, że jest to tablica `char`, nie ciągu zakończonego wartością null.  
  
```C  
// C4295.c
// compile with: /W4


int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
