---
title: "Wywoływanie funkcji DLL z aplikacji języka Visual Basic | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- functions [C++], calling DLL functions from Visual Basic
- DLL functions [C++]
- function calls [C++], DLL functions
- DLLs [C++], calling
- calling DLL functions from VB applications [C++]
- __stdcall keyword [C++]
- DLL functions [C++], calling
ms.assetid: 282f7fbf-a0f2-4b9f-b277-1982710be56c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 471f0b2b89d8c44f17567dd9af6add535be7fbcf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="calling-dll-functions-from-visual-basic-applications"></a>Wywoływanie funkcji DLL z aplikacji języka Visual Basic
Dla aplikacji Visual Basic (lub aplikacji w innych językach, takich jak Pascal lub Fortran) wywołanie funkcji w bibliotece DLL C/C++ można wyeksportować funkcji przy użyciu konwencji wywoływania poprawne bez żadnych nazwij dekorację wykonywane przez kompilator.  
  
 `__stdcall`Tworzy poprawne konwencji wywołania funkcji (wywołana funkcja czyści stosu i parametry są przekazywane od prawej do lewej), ale inaczej decorates nazwę funkcji. Tak, gdy **__declspec(dllexport)** jest używany na wyeksportowanej funkcji DLL nazwa jest eksportowany.  
  
 `__stdcall` Nazwij dekorację prefiksy nazwy symbolu od znaku podkreślenia (_) i dołącza symbol o znak @ (@) znak następuje liczba bajtów w liście argumentów (miejsca wymaganego stosu). Dzięki temu funkcja po zadeklarowaniu jako:  
  
```  
int __stdcall func (int a, double b)  
```  
  
 jest oznaczone jako:  
  
```  
_func@12  
```  
  
 Konwencja wywoływania C (`__cdecl`) decorates nazwę jako `_func`.  
  
 Aby uzyskać nazwa, należy użyć [/MAP](../build/reference/map-generate-mapfile.md). Użycie **__declspec(dllexport)** wykonuje następujące czynności:  
  
-   Jeśli funkcja jest wyeksportowany z konwencji wywoływania C (**_cdecl**), pasków wiodące podkreślenia (_), po wyeksportowaniu nazwę.  
  
-   Jeśli funkcja eksportowane nie używa konwencji wywoływania C (na przykład `__stdcall`), jego Eksportuje również nazwa.  
  
 Ponieważ nie ma sposobu na zastąpienie, w którym przeprowadzane jest oczyszczanie stosu, należy użyć `__stdcall`. Aby undecorate nazw z `__stdcall`, należy je określić za pomocą aliasów w sekcji eksportu pliku .def. Przedstawiono to w następujący sposób dla deklaracji następujących funkcji:  
  
```  
int  __stdcall MyFunc (int a, double b);  
void __stdcall InitCode (void);  
```  
  
 W. Plik DEF:  
  
```  
EXPORTS  
   MYFUNC=_MyFunc@12  
   INITCODE=_InitCode@0  
```  
  
 Biblioteki dll do wywołania przez programów napisanych w języku Visual Basic potrzeby technika alias wyświetlane w tym temacie w pliku .def. Alias jest wykonywana w programie Visual Basic, Użyj aliasu w pliku .def nie jest konieczne. Mogą to robić w programie Visual Basic, dodając klauzulę alias do [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement) instrukcji.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)  
  
-   [Eksportowanie z biblioteki DLL przy użyciu. Pliki DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Ustalanie, jakiej metody eksportu użyć](../build/determining-which-exporting-method-to-use.md)  
  
-   [Nazwy ozdobione](../build/reference/decorated-names.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki dll w programie Visual C++](../build/dlls-in-visual-cpp.md)