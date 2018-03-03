---
title: "Kompilatora (poziom 4) ostrzeżenie C4001 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4001
dev_langs:
- C++
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3b5c3d82bef81ee84514b39a0ce8ab07ad6e6c36
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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