---
title: "C4335 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4335
dev_langs: C++
helpviewer_keywords: C4335
ms.assetid: e66467ad-a10b-4438-8c7c-e8e8d11d39bb
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ab7406a9c161d47e431cb0af8183d99eac7bfe86
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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