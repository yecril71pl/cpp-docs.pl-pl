---
title: "C2011 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2011
dev_langs: C++
helpviewer_keywords: C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c599d6add1fa51c6aae7f04019eacdc94f11bb15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2011"></a>C2011 błąd kompilatora
'Identyfikator': 'type' wpisz ponowna definicja  
  
 Identyfikator został już zdefiniowany jako `type`. Sprawdź, czy definicji(-e) klas identyfikatora.  
  
 Możesz również uzyskać C2011 czy zaimportować plik nagłówka biblioteki typów więcej niż raz do tego samego pliku. Aby zapobiec dołączenia wiele typów zdefiniowanych w pliku nagłówka, użyj obejmują osłony lub `#pragma` [po](../../preprocessor/once.md) dyrektywy w pliku nagłówka.  
  
 Jeśli potrzebujesz można znaleźć w początkowej deklaracji typu zmieniony, możesz użyć [/P](../../build/reference/p-preprocess-to-a-file.md) flagi kompilatora do generowania wstępnie przetworzonych danych wyjściowych przekazane do kompilatora. Można użyć narzędzia wyszukiwania tekstu można znaleźć wystąpienia identyfikatora ponownie zdefiniowany w pliku wyjściowym.  
  
 Poniższy przykład generuje C2011 i przedstawia sposób rozwiązywanie problemu:  
  
```  
// C2011.cpp  
// compile with: /c  
struct S;  
union S;   // C2011  
union S2;   // OK  
```