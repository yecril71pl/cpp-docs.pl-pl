---
title: C4335 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4335
dev_langs:
- C++
helpviewer_keywords:
- C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adb8a7b484ce0946f385c3b2a8669ba1b5ccf0d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4335"></a>C4335 ostrzeżenia kompilatora
Wykryto format pliku Mac: Skonwertuj plik źródłowy do formatu DOS lub systemu UNIX  
  
 Znak zakończenia wiersza pierwszego wiersza pliku źródłowego jest styl Macintosh (\r) zamiast systemu UNIX (\n) lub DOS ("\r\n").  
  
 To zawsze ostrzeżenie jako błąd.  Zobacz [ostrzeżenie](../../preprocessor/warning.md) pragma informacji o sposobie Wyłącz to ostrzeżenie.  Ponadto to tylko ostrzeżenie raz na compiland. W związku z tym jeśli dostępnych jest wiele `#include` dyrektywy, które określają pliki w formacie Macintosh C4335 będzie być wystawiane tylko raz.  
  
 Jednym ze sposobów na wygenerowanie plików w formacie Macintosh jest przy użyciu **zaawansowane opcje zapisywania** (na **pliku** menu) w programie Visual Studio.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4335.  
  
```  
// C4335 expected  
#include "c4335.h"   // assume both include files are in Macintosh format  
#include "c4335_2.h"  
```