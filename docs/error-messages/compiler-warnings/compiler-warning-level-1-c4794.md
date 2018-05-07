---
title: Kompilatora (poziom 1) ostrzeżenie C4794 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4794
dev_langs:
- C++
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88ffa1200e7c760f028549335f0df5a9ea8ba3d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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