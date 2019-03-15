---
title: Ustalić, jakiej metody eksportu użyć
ms.date: 11/04/2016
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- exporting DLLs [C++], method comparison
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
ms.assetid: 66d773ed-935c-45c2-ad03-1a060874b34d
ms.openlocfilehash: 974c32cef87801599ba0d14fd146e84ad874467f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816298"
---
# <a name="determine-which-exporting-method-to-use"></a>Ustalić, jakiej metody eksportu użyć

Możesz wyeksportować funkcje na dwa sposoby — plik .def lub `__declspec(dllexport)` — słowo kluczowe. Aby pomóc w podjęciu decyzji, w jaki sposób jest lepszym rozwiązaniem dla biblioteki DLL, należy wziąć pod uwagę następujące pytania:

- Masz zamiar wyeksportować później więcej funkcji?

- Jest używane tylko przez aplikacje, które można odtworzyć lub jest on używany przez aplikacje, których nie można odbudować biblioteki DLL — na przykład w przypadku aplikacji, które są tworzone przez strony trzecie?

## <a name="pros-and-cons-of-using-def-files"></a>Zalet i wad za pomocą plików .def

Eksportowanie funkcji daje pliku .def, kontrolować eksportowe liczebniki porządkowe. Po dodaniu eksportowanych funkcji do biblioteki DLL, można przypisać wartości porządkowe większej niż eksportowanych funkcji. Gdy to zrobisz, aplikacje, które używają niejawna Konsolidacja nie trzeba ponownie połączyć z biblioteką importu, który zawiera nową funkcję. Jest to bardzo wygodne w przypadku projektowania DLL do użytku przez wiele aplikacji, ponieważ możesz dodawać nowe funkcje i upewnij się również, że będzie on nadal działać poprawnie z aplikacjami, które już polegać na niej. Na przykład biblioteki MFC DLL są kompilowane za pomocą plików .def.

Inną zaletą używania pliku .def jest, że można użyć `NONAME` atrybutu, aby wyeksportować funkcji. Spowoduje to umieszczenie tylko numer porządkowy w tabeli eksportu biblioteki DLL. Dla bibliotek DLL, które mają dużą liczbę eksportowanych funkcji przy użyciu `NONAME` atrybutów można zmniejszyć rozmiar pliku DLL. Aby uzyskać informacje na temat pisania instrukcji definicji modułu, zobacz [zasady dla instrukcji definicji modułu](reference/rules-for-module-definition-statements.md). Aby uzyskać informacji na temat Eksport porządkowej, zobacz [eksportowanie funkcji z biblioteki DLL według liczby porządkowej zamiast nazwy](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

Używając pliku .def wadą jest to czy jeśli eksportujesz funkcje w pliku C++, albo musisz umieścić nazwy dekorowane w .def pliku lub zdefiniować eksportowane funkcji za pomocą extern "C", aby uniknąć dekorowania nazwy, która została wykonana za pomocą kompilatora MSVC.

Umieszczenie nazwy dekorowane w pliku .def, możesz je uzyskać, korzystając z [DUMPBIN](reference/dumpbin-reference.md) narzędzia lub przy użyciu konsolidator [/MAP](reference/map-generate-mapfile.md) opcji. Nazwy dekoracyjne, które są produkowane przez kompilator są specyficzne dla kompilatora; w związku z tym, jeśli nazwy dekorowane, które są produkowane przez kompilator w pliku .def, aplikacje, które łącze do biblioteki DLL muszą być także kompilowane przy użyciu tej samej wersji kompilatora, aby nazwy dekorowane w aplikacji wywołującej odpowiadały wyeksportowany nazwy i n pliku .def biblioteki dll.

## <a name="pros-and-cons-of-using-declspecdllexport"></a>Zalet i wad przy użyciu atrybutu __declspec(dllexport)

Za pomocą `__declspec(dllexport)` jest wygodne, ponieważ nie masz już martwić się o obsługę pliku .def i uzyskiwanie nazwy dekorowane eksportowanych funkcji. Jednak użyteczności w ten sposób eksportowania jest ograniczona przez liczbę połączonych aplikacji, które chcesz ponownie skompilować. Po odbudowaniu biblioteki DLL za pomocą nowego eksportu należy odbudować aplikacji, ponieważ nazwy dekorowane dla wyeksportowanych funkcji C++ mogą ulec zmianie, jeśli używasz innej wersji kompilatora, aby skompilować go ponownie.

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL za pomocą. Pliki DEF](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Eksportuj funkcje C++ do użycia w plikach wykonywalnych języka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Eksportuj funkcje C do użycia w plikach wykonywalnych języka C lub języka C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Zainicjuj bibliotekę DLL](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Importowanie i eksportowanie funkcji śródwierszowych](importing-and-exporting-inline-functions.md)

- [Importy wzajemne](mutual-imports.md)

- [Nazwy ozdobione](reference/decorated-names.md)

## <a name="see-also"></a>Zobacz także

[Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)
