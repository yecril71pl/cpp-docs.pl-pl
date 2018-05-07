---
title: Kompilatora (poziom 4) ostrzeżenie C4001 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4001
dev_langs:
- C++
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc728fa5c66fb4b42c8fe4a785f36048ffbaed4e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4001"></a>Kompilator C4001 ostrzegawcze (poziom 4)
użyto niestandardowego rozszerzenia 'single line comment' została użyta.  

> [!NOTE] 
> To ostrzeżenie zostanie usunięty w programie Visual Studio 2017 wersji 15,5 cala, ponieważ komentarz jednowierszowy są standardowymi C99.
  
 Komentarz jednowierszowy są standard języka C++ i standard w C począwszy C99. W obszarze strict zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), pliki C, które zawierają komentarz jednowierszowy Generowanie C4001 ze względu na użycie niestandardowe rozszerzenia. Ponieważ komentarz jednowierszowy standard języka C++, C pliki zawierające komentarz jednowierszowy nie daje C4001 podczas kompilowania przy użyciu rozszerzenia Microsoft (/Ze).  
  
## <a name="example"></a>Przykład  
 Aby wyłączyć ostrzeżenie, usuń znaczniki komentarza [#pragma warning(disable:4001)](../../preprocessor/warning.md).  
  
```  
// C4001.cpp  
// compile with: /W4 /Za /TC  
// #pragma warning(disable:4001)  
int main()  
{  
   // single-line comment in main  
   // C4001  
}  
```