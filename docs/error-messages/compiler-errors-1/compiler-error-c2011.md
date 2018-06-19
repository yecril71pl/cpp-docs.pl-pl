---
title: C2011 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2011
dev_langs:
- C++
helpviewer_keywords:
- C2011
ms.assetid: 992c9d51-e850-4d53-b86b-02e73b38249c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 898a724f022a81f590ec1f8165de9752de6c1d0b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33166640"
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