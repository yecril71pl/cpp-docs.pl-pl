---
title: "Kompilatora (poziom 1) ostrzeżenie C4789 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4789
dev_langs: C++
helpviewer_keywords: C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 673d1059babf9e14528711053fd97686e3add1cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4789"></a>Kompilator C4789 ostrzegawcze (poziom 1)
Bufor identyfikator i N bajtów zostanie przepełniony; M bajtów zostanie zapisane zaczynając od przesunięcia L  
  
 Ostrzega o przepełnienie w przypadku określonych funkcji (CRT) środowiska wykonawczego języka C buforu parametry są przekazywane i wykonywane są przypisania, taki sposób, że rozmiar danych są określane w czasie kompilacji. To ostrzeżenie jest odpowiednie do sytuacji, które mogą elude typowe niezgodność rozmiaru danych wykrywania.  
  
 Ostrzeżenie jest wyświetlane podczas danych, której długość jest znany w czas kompilacji, jest kopiowany i umieścić w bloku danych, którego rozmiar jest znany w czasie kompilacji będzie zbyt mała danych. Kopia musi odbywać się za pomocą formularza — wewnętrzne jednej z następujących funkcji CRT:  
  
-   [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)  
  
-   [funkcji memset](../../c-runtime-library/reference/memset-wmemset.md)  
  
-   [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md), [wmemcpy —](../../c-runtime-library/reference/memcpy-wmemcpy.md)  
  
 Ostrzeżenie jest wyświetlane, gdy Niedopasowany typ danych parametru za pomocą rzutowanie, a następnie próby przypisania kopiowania z odwołania do wartości.  
  
 Visual C++ może generować to ostrzeżenie dla ścieżki kodu, który nigdy nie wykonuje. To ostrzeżenie można tymczasowo wyłączyć za pomocą `#pragma`, jak pokazano w poniższym przykładzie:  
  
 `#pragma(push)`  
  
 `#pragma warning ( disable : 4789 )`  
  
 `// unused code that generates compiler warning C4789`  
  
 `#pragma(pop)`  
  
 Dzięki temu Visual C++ na generowanie ostrzeżenia dla tego określonego bloku kodu. `#pragma(push)` Zachowuje istniejące stanu przed `#pragma warning(disable: 4789)` zmianę. `#pragma(pop)` Przywraca stan wypychanie i usuwa skutków `#pragma warning(disable:4789)`. Aby uzyskać więcej informacji na temat dyrektywy preprocesora C++ `#pragma`, zobacz [ostrzeżenie](../../preprocessor/warning.md) i [dyrektywy Pragma i słowo kluczowe __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4789.  
  
```  
// C4789.cpp  
// compile with: /Oi /W1 /c  
#include <string.h>  
#include <stdio.h>  
  
int main()   
{  
    char a[20];  
    strcpy(a, "0000000000000000000000000\n");   // C4789  
  
    char buf2[20];  
    memset(buf2, 'a', 21);   // C4789  
  
    char c;  
    wchar_t w = 0;  
    memcpy(&c, &w, sizeof(wchar_t));  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje również C4789.  
  
```  
// C4789b.cpp  
// compile with: /W1 /O2 /c  
// processor: x86  
short G;  
  
void main()  
{  
   int * p = (int *)&G;   
   *p = 3;   // C4789 - writes an int through a pointer to short  
}   
```