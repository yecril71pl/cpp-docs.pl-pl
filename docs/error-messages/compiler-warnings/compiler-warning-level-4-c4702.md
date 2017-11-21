---
title: "Kompilatora (poziom 4) ostrzeżenie C4702 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4702
dev_langs: C++
helpviewer_keywords: C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ffb7dd376881b36bbf70b5e64f646aaf3f112552
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4702"></a>Kompilator C4702 ostrzegawcze (poziom 4)
nieosiągalny kod  
  
 To ostrzeżenie jest wynikiem pracy zgodność kompilatora, która została wykonana dla programu Visual Studio .NET 2003: nieosiągalny kod. Kompilator (zaplecza) wykrycie nieosiągalny kod zostanie wygenerowany C4702, ostrzeżenie poziom 4.  
  
 Kod, który jest prawidłowy w wersjach programu Visual Studio .NET 2003 i Visual Studio .NET programu Visual C++ Usuń nieosiągalny kod lub mieć pewność, że wszystkie kod źródłowy jest dostępny za niektóre przepływ wykonania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4702.  
  
```  
// C4702.cpp  
// compile with: /W4  
#include <stdio.h>  
  
int main() {  
   return 1;  
   printf_s("I won't print.\n");   // C4702 unreachable  
}  
```  
  
## <a name="example"></a>Przykład  
 Podczas kompilowania za pomocą **/GX**, **opcja/ehc**, **/ehsc**, lub **/EHac** i przy użyciu zewnętrzne funkcje C, kod może stać się niedostępne ponieważ extern C funkcje są zakłada się, że nie zgłosi wyjątku, w związku z tym blok catch nie jest dostępny.  Jeśli uważasz, że to ostrzeżenie jest nieprawidłowy, ponieważ funkcja może zgłosić, kompilacji z **/eha** lub **/EHS**, w zależności od zgłoszono wyjątek.  
  
 Aby uzyskać więcej informacji, zobacz [/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C4702.  
  
```  
// C4702b.cpp  
// compile with: /W4 /EHsc  
#include <iostream>  
  
using namespace std;  
extern "C" __declspec(dllexport) void Function2(){}  
  
int main() {  
   try {  
      Function2();  
   }  
   catch (...) {  
      cout << "Exp: Function2!" << endl;   // C4702  
   }  
}  
```