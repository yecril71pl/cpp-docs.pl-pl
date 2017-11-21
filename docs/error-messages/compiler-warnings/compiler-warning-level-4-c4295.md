---
title: "Kompilatora (poziom 4) ostrzeżenie C4295 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
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
ms.openlocfilehash: 5815aab6163c7dc6ffa8bf89bbf56259724d02b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4295"></a>Kompilator C4295 ostrzegawcze (poziom 4)
  
> "*tablicy*": tablica jest zbyt mała, aby uwzględnić znak końcowy null  
  
 Tablica został zainicjowany, ale ostatni znak w tablicy nie jest wartość null; Uzyskiwanie dostępu do tablicy może dać nieoczekiwane wyniki.  
  
## <a name="example"></a>Przykład  
  
 Poniższy przykład generuje C4295. Aby rozwiązać ten problem, można deklarowaniu rozmiar tablicy większy, aby pomieścić kończącym null z inicjatora.  
  
```C  
// C4295.c  
// compile with: /W4  
  
int main() {  
   char a[3] = "abc";   // C4295  
}  
```