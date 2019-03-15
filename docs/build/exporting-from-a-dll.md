---
title: Eksportowanie z biblioteki DLL
ms.date: 11/04/2016
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
ms.openlocfilehash: 6bdf5b86724ae07aa073a9feb1cc4d5723bc6e6b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819121"
---
# <a name="exporting-from-a-dll"></a>Eksportowanie z biblioteki DLL

Plik DLL ma bardzo podobne do pliku .exe, z jedną istotną różnicą układ — plik DLL zawiera tabelę eksportu. Tabela eksportów zawiera nazwę każdej funkcji, która eksporty biblioteki DLL do innych plików wykonywalnych. Te funkcje są punkty wejścia w DLL; tylko funkcje w tabeli eksportu jest możliwy przez inne pliki wykonywalne. Wszystkie inne funkcje w bibliotece DLL są prywatne do biblioteki DLL. W tabeli eksportu biblioteki dll mogą być wyświetlane za pomocą [DUMPBIN](reference/dumpbin-reference.md) narzędzia z opcją/EXPORTS.

Możesz wyeksportować funkcje z biblioteki DLL przy użyciu dwóch metod:

- Utwórz plik definicji (.def) modułu i użyj pliku .def, podczas kompilowania biblioteki DLL. Tej metody należy użyć, jeśli chcesz [eksportowanie funkcji z biblioteki DLL według numeru porządkowego a nie nazwy](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

- Użyj słowa kluczowego **__declspec(dllexport)** w definicji funkcji.

Podczas eksportowania funkcji z jednej z metod, upewnij się, że używasz [__stdcall](../cpp/stdcall.md) konwencji wywoływania.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL za pomocą plików .def](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Eksportuj funkcje C++ do użycia w plikach wykonywalnych języka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Eksportuj funkcje C do użycia w plikach wykonywalnych języka C lub języka C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Eksportowanie funkcji z biblioteki DLL według numeru porządkowego a nie nazwy](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [Określić, której metody eksportowania użyjesz](determining-which-exporting-method-to-use.md)

- [Łączenie pliku wykonywalnego z biblioteką DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [Zainicjuj bibliotekę DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Importowanie do aplikacji](importing-into-an-application.md)

- [Importowanie i eksportowanie funkcji śródwierszowych](importing-and-exporting-inline-functions.md)

- [Importy wzajemne](mutual-imports.md)

## <a name="see-also"></a>Zobacz także

[Importowanie i eksportowanie](importing-and-exporting.md)
