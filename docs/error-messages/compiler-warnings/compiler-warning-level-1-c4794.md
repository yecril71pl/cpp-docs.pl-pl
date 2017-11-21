---
title: "Kompilatora (poziom 1) ostrzeżenie C4794 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4794
dev_langs: C++
helpviewer_keywords: C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cd5c04107afefca59b84059330b6b0b891b974e9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4794"></a>Kompilator C4794 ostrzegawcze (poziom 1)
segment zmiennej magazynu lokalnego wątku "Zmienna" zmiany z "Nazwa sekcji" na ".tls$"  
  
 Możesz użyć [#pragma data_seg](../../preprocessor/data-seg.md) mają zostać umieszczone w sekcji nie uruchamia się od .tls$ zmienną tls.  
  
 .Tls$*x* sekcji będzie istnieć w pliku obiektu gdzie [__declspec(thread)](../../cpp/thread.md) zdefiniowanych zmiennych. Sekcja .tls plik EXE lub DLL spowoduje z tych sekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4794:  
  
```  
// C4794.cpp  
// compile with: /W1 /c  
#pragma data_seg(".someseg")  
__declspec(thread) int i;   // C4794  
  
// OK  
#pragma data_seg(".tls$9")  
__declspec(thread) int j;  
```