---
title: "Kompilatora (poziom 4) ostrzeżenie C4295 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 1/09/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4295
dev_langs: C++
helpviewer_keywords: C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 56ffdce8c2790a3944a8f79753177bc80e249778
ms.sourcegitcommit: bc086a7acbe2d9fd77d115f269cc2a0dbeeb5b88
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
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
