---
title: Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- dllexport
- __declspec
dev_langs:
- C++
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6ab1d11c117c75633ce4ab836965449c4cc6ca1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="exporting-from-a-dll-using-declspecdllexport"></a>Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)
Microsoft wprowadzone **__export** w wersji 16-bitowych kompilatora Visual C++, aby umożliwić kompilator, aby automatycznie wygenerować nazw eksportu i umieścić je w pliku lib. Ten plik lib można tak samo jak statycznej lib do łączenia z biblioteki DLL.  
  
 W nowszych wersji kompilatora, można wyeksportować danych, funkcji, klas lub funkcji elementów członkowskich klasy z biblioteki DLL przy użyciu **__declspec(dllexport)** — słowo kluczowe. **__declspec(dllexport)** dodaje dyrektywy eksportu pliku obiektu, dzięki czemu nie trzeba używać plik .def.  
  
 Ta wygody są najbardziej widoczne, gdy próba eksportu dekorowane nazwy funkcji języka C++. Ponieważ nie istnieje standardowa specyfikacja dekoracji nazwy, wersji kompilatora może zmienić nazwy wyeksportowanej funkcji. Jeśli używasz **__declspec(dllexport)**, ponowną kompilację biblioteki DLL i plików zależnych .exe jest konieczne tylko konta zmiany konwencji nazewnictwa.  
  
 Wiele wyeksportować dyrektywy, takie jak porządkowe, NONAME i prywatny, jest możliwe tylko w pliku .def i nie ma sposobu na określenie tych atrybutów bez plik .def. Jednak przy użyciu **__declspec(dllexport)** oprócz przy użyciu .def pliku nie powoduje błędy kompilacji.  
  
 Aby wyeksportować funkcje, **__declspec(dllexport)** — słowo kluczowe musi występować w lewo Konwencja wywoływania — słowo kluczowe, jeśli jest określone słowo kluczowe. Na przykład:  
  
```  
__declspec(dllexport) void __cdecl Function1(void);  
```  
  
 Aby wyeksportować wszystkie publiczne elementy członkowskie danych i funkcji Członkowskich w klasie, słowo kluczowe muszą znajdować się na lewo od nazwy klasy w następujący sposób:  
  
```  
class __declspec(dllexport) CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
> [!NOTE]
>  `__declspec(dllexport)` Nie można zastosować do funkcji z `__clrcall` konwencji wywoływania.  
  
 Podczas tworzenia biblioteki DLL, zwykle Utwórz plik nagłówka zawierający prototypy funkcji i/lub klasy są eksportowane i Dodaj **__declspec(dllexport)** deklaracje w pliku nagłówka. Aby zwiększyć czytelność kodu, zdefiniuj makro **__declspec(dllexport)** i makra za pomocą każdej symbol w przypadku eksportowania:  
  
```  
#define DllExport   __declspec( dllexport )   
```  
  
 **__declspec(dllexport)** magazynów funkcji nazwy tabeli eksportu biblioteki DLL. Jeśli chcesz zoptymalizować rozmiar tabeli, zobacz [eksportowanie funkcji z biblioteki DLL przez numer, a nie według nazwy](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
> [!NOTE]
>  Podczas przenoszenia biblioteki DLL kodu źródłowego z Win16 do systemu Win32, Zastąp każde wystąpienie **__export** z **__declspec(dllexport)**.  
  
 Jako odwołanie Przeszukaj plik nagłówka Win32 Winbase.h. Zawiera przykłady **__declspec(dllimport)** użycia.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Eksportowanie z biblioteki DLL przy użyciu .def — pliki](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Eksportowanie funkcji języka C do użycia w plikach wykonywalnych języka C lub języka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Określić jakiej metody eksportu użyć](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicjowanie biblioteki DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [__Declspec — słowo kluczowe](../cpp/declspec.md)  
  
-   [Importowanie i eksportowanie funkcji śródwierszowych](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importy wzajemne](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)