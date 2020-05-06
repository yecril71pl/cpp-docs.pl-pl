---
title: Wybieranie metody eksportowania do użycia
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
ms.openlocfilehash: 974c32cef87801599ba0d14fd146e84ad874467f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273740"
---
# <a name="determine-which-exporting-method-to-use"></a>Wybieranie metody eksportowania do użycia

Funkcje można eksportować na jeden z dwóch sposobów — plik. def lub `__declspec(dllexport)` słowo kluczowe. Aby ułatwić podjęcie decyzji, która metoda jest lepsza dla biblioteki DLL, należy wziąć pod uwagę następujące pytania:

- Czy planujesz wyeksportować więcej funkcji później?

- Czy biblioteka DLL jest używana tylko przez aplikacje, które można skompilować lub które są używane przez aplikacje, których nie można skompilować ponownie — na przykład aplikacje, które są tworzone przez strony trzecie?

## <a name="pros-and-cons-of-using-def-files"></a>Specjaliści i wady dotyczące korzystania z plików. def

Eksportowanie funkcji w pliku. def daje kontrolę nad numerami eksportu. Po dodaniu wyeksportowanej funkcji do biblioteki DLL można przypisać jej wyższą wartość porządkową niż jakakolwiek inna funkcja eksportowana. Po wykonaniu tej czynności aplikacje korzystające z niejawnego łączenia nie muszą ponownie łączyć się z biblioteką importu, która zawiera nową funkcję. Jest to bardzo wygodne, jeśli projektujesz bibliotekę DLL do użytku przez wiele aplikacji, ponieważ możesz dodać nowe funkcje, a także upewnić się, że nadal działają poprawnie z aplikacjami, które są już na nim zależne. Na przykład biblioteki DLL MFC są kompilowane przy użyciu plików. def.

Inną możliwością użycia pliku. def jest użycie `NONAME` atrybutu do eksportowania funkcji. Spowoduje to umieszczenie tylko liczby porządkowej w tabeli eksportów biblioteki DLL. W przypadku bibliotek DLL, które mają dużą liczbę wyeksportowanych funkcji `NONAME` , użycie atrybutu może zmniejszyć rozmiar pliku dll. Aby uzyskać informacje dotyczące sposobu pisania instrukcji modułu definicji, zobacz [reguły dotyczące instrukcji definicji modułów](reference/rules-for-module-definition-statements.md). Aby uzyskać informacje na temat eksportu porządkowego, zobacz [Eksportowanie funkcji z biblioteki DLL według liczby porządkowej, a nie nazwy](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

Wadą użycia pliku. def jest to, że jeśli eksportujesz funkcje w pliku języka C++, musisz umieścić nazwy dekoracyjne w pliku. def lub zdefiniować eksportowane funkcje przy użyciu extern "C", aby uniknąć dekoracji nazw, które jest wykonywane przez kompilator MSVC.

Jeśli umieścisz nazwy dekoracyjne w pliku. def, możesz je uzyskać za pomocą narzędzia [polecenia DUMPBIN](reference/dumpbin-reference.md) lub za pomocą opcji konsolidatora [/map](reference/map-generate-mapfile.md) . Nazwy dekoracyjne, które są tworzone przez kompilator, są specyficzne dla kompilatora; w związku z tym, jeśli umieścisz dekoracyjne nazwy, które są tworzone przez kompilator w pliku. def, aplikacje łączące się z biblioteką DLL również muszą być kompilowane przy użyciu tej samej wersji kompilatora, aby nazwy dekoracyjne w aplikacji wywołującej były zgodne z wyeksportowanymi nazwami w pliku. def biblioteki DLL.

## <a name="pros-and-cons-of-using-__declspecdllexport"></a>Specjaliści i wady korzystania z __declspec (dllexport)

Korzystanie `__declspec(dllexport)` z programu jest wygodne, ponieważ nie trzeba martwić się o utrzymywanie pliku. def i uzyskanie nazw dekoracyjnych funkcji eksportowanych. Jednak użyteczność tego sposobu eksportowania jest ograniczona przez liczbę połączonych aplikacji, które chcesz ponownie skompilować. W przypadku odbudowywania biblioteki DLL przy użyciu nowych eksportów należy również ponownie skompilować aplikacje, ponieważ nazwy dekoracyjne dla eksportowanych funkcji języka C++ mogą ulec zmianie, jeśli używasz innej wersji kompilatora do jej odbudowania.

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL przy użyciu programu. Pliki DEF](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Eksportowanie funkcji C do użycia w plikach wykonywalnych języka C lub C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicjowanie biblioteki DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Importowanie i eksportowanie funkcji śródwierszowych](importing-and-exporting-inline-functions.md)

- [Importy wzajemne](mutual-imports.md)

- [Nazwy dekoracyjne](reference/decorated-names.md)

## <a name="see-also"></a>Zobacz też

[Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)
