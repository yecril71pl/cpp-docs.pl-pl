---
title: "Błąd narzędzi konsolidatora LNK2011 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2011
dev_langs:
- C++
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9811bdb905df61bb77ea4af6bc4ced7c4ba42106
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2011"></a>Błąd narzędzi konsolidatora LNK2011
wstępnie skompilowany obiekt nie jest połączony. Obraz może nie działać.  
  
 Jeśli używasz prekompilowanych nagłówków łącze wymaga muszą być wszystkie pliki obiektów utworzonych za pomocą prekompilowane nagłówki połączone w. Jeśli masz plik źródłowy, który służy do generowania prekompilowanego nagłówka do użycia z innych plików źródłowych, teraz należy dołączyć plik obiektu utworzony wraz prekompilowanego nagłówka.  
  
 Na przykład jeśli należy skompilować plik o nazwie STUB.cpp do utworzenia prekompilowanego nagłówka do użycia z innych plików źródłowych, należy połączyć z STUB.obj lub otrzymasz ten błąd. W następujących wierszy polecenia wiersza jeden służy do tworzenia prekompilowanego nagłówka, COMMON.pch, który jest używany z PROG1.cpp i PROG2.cpp w wierszach, 2 i 3. Plik STUB.cpp zawiera tylko `#include` wierszy (takie same `#include` wierszy PROG1.cpp i PROG2.cpp) i jest używany tylko do wygenerowania prekompilowanych nagłówków. W ostatnim wierszu STUB.obj musi być połączony w celu uniknięcia LNK2011.  
  
```  
cl /c /Yccommon.h stub.cpp  
cl /c /Yucommon.h prog1.cpp  
cl /c /Yucommon.h prog2.cpp  
link /out:prog.exe stub.obj prog1.obj prog2.obj  
```