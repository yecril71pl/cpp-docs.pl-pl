---
title: "C2813 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1eb1d5a0175cb151735c7799d10403cf8eac4944
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2813"></a>C2813 błąd kompilatora
\#Import nie jest obsługiwany z /MP  
  
 C2813 jest wysyłanego w poleceniu kompilatora określenia **/MP** — opcja kompilatora i co najmniej dwa pliki do kompilacji i co najmniej jeden z plików zawiera[#import](../../preprocessor/hash-import-directive-cpp.md) dyrektywy preprocesora. [#Import](../../preprocessor/hash-import-directive-cpp.md) dyrektywy generuje klasy C++ z typów w określonej biblioteki typów, a następnie zapisuje te klasy dwa pliki nagłówka. [#Import](../../preprocessor/hash-import-directive-cpp.md) dyrektywy nie jest obsługiwana, ponieważ w wielu jednostkach kompilacji zaimportować tę samą bibliotekę typów, te jednostki spowodować konflikt podczas próby zapisania tych samych plików nagłówka w tym samym czasie.  
  
 Ten błąd kompilatora i **/MP** — opcja kompilatora są nowością w programie Visual Studio 2008.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C2813. W wierszu polecenia "Kompiluj z użyciem:" komentarz informuje kompilator, aby używał **/MP** i **/c** — opcje kompilatora do kompilowania wielu plików. Zawiera co najmniej jeden z plików [#import](../../preprocessor/hash-import-directive-cpp.md) dyrektywy. Możemy użyć tego samego pliku dwukrotnie w celu testowania w tym przykładzie.  
  
```  
// C2813.cpp  
// compile with: /MP /c C2813.cpp C2813.cpp  
#import "C:\windows\system32\stdole2.tlb"   // C2813  
int main()   
{  
}  
```