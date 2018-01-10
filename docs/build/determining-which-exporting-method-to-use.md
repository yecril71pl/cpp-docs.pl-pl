---
title: "Ustalanie, jakiej metody eksportu użyć | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7375d4baf31c1564493fd29938ef2ac8ee034f3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="determining-which-exporting-method-to-use"></a>Ustalanie, jakiej metody eksportu użyć
Możesz wyeksportować funkcje na dwa sposoby — plik .def lub `__declspec(dllexport)` — słowo kluczowe. Aby określić, w jaki sposób jest lepszym rozwiązaniem dla biblioteki DLL, należy rozważyć następujące kwestie:  
  
-   Czy firma planuje wyeksportować więcej funkcji później?  
  
-   Biblioteki DLL używane tylko przez aplikacje, które można odtworzyć lub jest on używany przez aplikacje, których nie można odbudować jest — na przykład aplikacje, które są tworzone przez osoby trzecie?  
  
## <a name="pros-and-cons-of-using-def-files"></a>Zalet i wad przy użyciu .def — pliki  
 Eksportowanie funkcji w zapewnia plik .def, kontrolować porządkowe eksportu. Po dodaniu wyeksportowanej funkcji do biblioteki DLL, można przypisać numer porządkowy wartość większą niż wyeksportowanej funkcji. Po wykonaniu tej aplikacji, które używają Konsolidacja niejawna nie trzeba ponownie połączyć z biblioteki importu, która zawiera nową funkcję. Jest to bardzo przydatne przy projektowania biblioteki DLL do użycia przez wiele aplikacji, ponieważ możesz dodać nowe funkcje i upewnij się również, że nadal działają poprawnie, aplikacje, które już od niej zależne. Na przykład biblioteki DLL MFC są tworzone za pomocą .def — pliki.  
  
 Inną zaletą używania plik .def jest, że można używać `NONAME` atrybutu, aby wyeksportować funkcji. Spowoduje to umieszczenie tylko numer porządkowy w tabeli eksportu w bibliotece DLL. Dla bibliotek DLL, które ma dużą liczbę eksportowane funkcje za pomocą `NONAME` atrybut można zmniejszyć rozmiar pliku DLL. Aby uzyskać informacje na temat pisania instrukcji definicji modułu, zobacz [zasady dla instrukcji definicji modułu](../build/reference/rules-for-module-definition-statements.md). Aby uzyskać informacje o liczbie porządkowej eksportu, zobacz [eksportowanie funkcji z biblioteki DLL według liczby porządkowej, a nie według nazwy](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
 Wadą przy użyciu pliku .def jest czy eksportowania funkcji w pliku języka C++, albo trzeba umieścić nazwy ozdobione w .def pliku lub zdefiniuj eksportowane funkcje za pomocą zewnętrzne "C", aby uniknąć nazwij dekorację, która została wykonana przez kompilator języka Visual C++.  
  
 Nazwy ozdobione umieszczenie w pliku .def, możesz uzyskać je za pomocą [DUMPBIN](../build/reference/dumpbin-reference.md) narzędzia lub przy użyciu konsolidator [/MAP](../build/reference/map-generate-mapfile.md) opcji. Nazwy ozdobione, które są tworzone przez kompilator są specyficzne dla kompilatora; w związku z tym umieszczenie nazwy ozdobione, które są tworzone przez kompilator do pliku .def, aplikacje, które łącze do pliku DLL muszą również zostać skompilowane przy użyciu tej samej wersji kompilatora, aby odpowiadały wyeksportowany nazwy ozdobione w aplikacji wywołującej nazwy i n plik .def biblioteki dll.  
  
## <a name="pros-and-cons-of-using-declspecdllexport"></a>Zalet i wad przy użyciu atrybutu __declspec(dllexport)  
 Przy użyciu `__declspec(dllexport)` jest wygodne, ponieważ nie trzeba martwić się o zachowaniu plik .def i uzyskanie nazwy ozdobione wyeksportowanej funkcji. Jednak przydatność ten sposób eksportowania jest ograniczona liczba połączonych aplikacji, które chcesz odbudować. Jeśli odbudować biblioteki DLL z nowego eksportu, należy odbudować aplikacji, ponieważ nazwy ozdobione dla eksportowanych funkcji C++ mogą ulec zmianie, jeśli używasz innej wersji kompilatora, aby skompilować go ponownie.  
  
### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Eksportowanie z biblioteki DLL przy użyciu. Pliki DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Eksportowanie funkcji języka C do użycia w plikach wykonywalnych języka C lub języka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicjowanie biblioteki DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Importowanie i eksportowanie funkcji śródwierszowych](../build/importing-and-exporting-inline-functions.md)  
  
-   [Importy wzajemne](../build/mutual-imports.md)  
  
-   [Nazwy ozdobione](../build/reference/decorated-names.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)