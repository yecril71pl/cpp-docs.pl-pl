---
title: Eksportowanie z biblioteki DLL przy użyciu plików DEF | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a870df7ea803813a8403cd807c0f0612873d4576
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="exporting-from-a-dll-using-def-files"></a>Eksportowanie z biblioteki DLL przy użyciu plików DEF
Plik definicji modułu (.def) to plik tekstowy zawierający co najmniej jeden moduł instrukcje opisujących różne atrybuty biblioteki dll. Jeśli nie używasz **__declspec(dllexport)** — słowo kluczowe, aby wyeksportować funkcji DLL plik .def wymaga biblioteki DLL.  
  
 Poniższe instrukcje definicji modułu musi zawierać plik .def minimalne:  
  
-   Pierwsza instrukcja w pliku musi być instrukcją biblioteki. Ta instrukcja wskazywany jest plik .def jako należące do biblioteki DLL. Instrukcja biblioteki następuje nazwa biblioteki dll. Konsolidator umieści tej nazwy w biblioteki importowanej biblioteki DLL.  
  
-   Instrukcję EXPORTS zawiera listę nazw i, opcjonalnie, wartości porządkowe funkcji wyeksportowane przez bibliotekę DLL. Przypisywać wartość porządkową funkcji wykonując nazwę funkcji z znak @ (@) i numer. Podczas określania wartości porządkowe muszą być z zakresu od 1 do N, gdzie N to liczba funkcje wyeksportowane przez bibliotekę DLL. Jeśli chcesz wyeksportować funkcji według liczby porządkowej, zobacz [eksportowanie funkcji z biblioteki DLL według liczby porządkowej, a nie według nazwy](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) oraz w tym temacie.  
  
 Na przykład bibliotekę DLL, która zawiera kod, aby zaimplementować drzewo binarne wyszukiwania może wyglądać następujące czynności:  
  
```  
LIBRARY   BTREE  
EXPORTS  
   Insert   @1  
   Delete   @2  
   Member   @3  
   Min   @4  
```  
  
 Jeśli używasz [Kreator biblioteki DLL MFC](../mfc/reference/mfc-dll-wizard.md) do tworzenia biblioteki MFC DLL, Kreator tworzy plik .def szkielet i automatycznie dodaje do projektu. Dodaj nazwy funkcji, które mają zostać wyeksportowane do tego pliku. Dll z systemem innym niż MFC, należy utworzyć plik .def samodzielnie i dodaj go do projektu.  
  
 Jeśli są eksportowane funkcje w pliku języka C++, należy umieścić nazwy ozdobione w pliku .def lub zdefiniuj wyeksportowanej funkcji z powiązaniem C standard za pomocą zewnętrzne "C". Jeśli chcesz umieścić w pliku .def nazwy ozdobione, możesz uzyskać je za pomocą [DUMPBIN](../build/reference/dumpbin-reference.md) narzędzia lub przy użyciu konsolidator [/MAP](../build/reference/map-generate-mapfile.md) opcji. Pamiętaj, że nazwy ozdobione generowane przez kompilator jest określonych kompilatora. Jeśli umieścisz nazwy ozdobione generowane przez kompilator języka Visual C++ do pliku .def aplikacje połączone biblioteki DLL muszą zostać skompilowane również, za pomocą tej samej wersji programu Visual C++, dzięki czemu nazwy ozdobione w aplikacji wywołującej odpowiadać nazwom wyeksportowanego w regionalne DLL Plik f.  
  
 Jeśli tworzysz [biblioteki DLL rozszerzenia](../build/extension-dlls-overview.md), i eksportowanie przy użyciu pliku .def, umieść następujący kod na początku i na końcu pliki nagłówka zawierające wyeksportowanej klasy:  
  
```  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 Te wiersze upewnij się, że MFC zmienne, które są używane wewnętrznie lub które są dodawane do klas są eksportowane (lub zaimportować) z bibliotekę DLL rozszerzenia MFC. Na przykład w przypadku tworzenia klasy pochodnej klasy przy użyciu `DECLARE_DYNAMIC`, rozszerza makra, aby dodać `CRuntimeClass` zmiennej członkowskiej do swojej klasy. Pozostawienie tych czterech wierszy może spowodować biblioteki DLL do kompilacji lub połączyć niepoprawnie lub spowodować błąd, jeśli aplikacja kliencka łącze do pliku DLL.  
  
 Podczas tworzenia biblioteki DLL, konsolidator używa plik .def, aby utworzyć plik eksportu (.exp) i pliku importu biblioteki (lib). Konsolidator następnie używa pliku eksportu do tworzenia pliku DLL. Pliki wykonywalne niejawnie połączyć link biblioteki DLL do biblioteki importu, jeśli zostały one utworzone.  
  
 Należy zwrócić uwagę na to, że MFC sam używa .def — pliki, aby wyeksportować klasy i funkcje z MFCx0.dll.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Eksportowanie funkcji języka C do użycia w plikach wykonywalnych języka C lub języka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Określić jakiej metody eksportu użyć](../build/determining-which-exporting-method-to-use.md)  
  
-   [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicjowanie biblioteki DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [.def — pliki](../build/reference/module-definition-dot-def-files.md)  
  
-   [Zasady dla instrukcji definicji modułu](../build/reference/rules-for-module-definition-statements.md)  
  
-   [Nazwy ozdobione](../build/reference/decorated-names.md)  
  
-   [Importowanie i eksportowanie funkcji śródwierszowych](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importy wzajemne](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)