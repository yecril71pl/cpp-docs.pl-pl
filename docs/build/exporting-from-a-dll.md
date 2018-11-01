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
ms.openlocfilehash: f932ba2d9b229d236270eb664ac1291725471706
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50493824"
---
# <a name="exporting-from-a-dll"></a>Eksportowanie z biblioteki DLL

Plik DLL ma bardzo podobne do pliku .exe, z jedną istotną różnicą układ — plik DLL zawiera tabelę eksportu. Tabela eksportów zawiera nazwę każdej funkcji, która eksporty biblioteki DLL do innych plików wykonywalnych. Te funkcje są punkty wejścia w DLL; tylko funkcje w tabeli eksportu jest możliwy przez inne pliki wykonywalne. Wszystkie inne funkcje w bibliotece DLL są prywatne do biblioteki DLL. W tabeli eksportu biblioteki dll mogą być wyświetlane za pomocą [DUMPBIN](../build/reference/dumpbin-reference.md) narzędzia z opcją/EXPORTS.

Możesz wyeksportować funkcje z biblioteki DLL przy użyciu dwóch metod:

- Utwórz plik definicji (.def) modułu i użyj pliku .def, podczas kompilowania biblioteki DLL. Tej metody należy użyć, jeśli chcesz [eksportowanie funkcji z biblioteki DLL według numeru porządkowego a nie nazwy](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

- Użyj słowa kluczowego **__declspec(dllexport)** w definicji funkcji.

Podczas eksportowania funkcji z jednej z metod, upewnij się, że używasz [__stdcall](../cpp/stdcall.md) konwencji wywoływania.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL za pomocą plików .def](../build/exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Eksportuj funkcje C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Eksportuj funkcje C do użycia w plikach wykonywalnych języka C lub języka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Eksportowanie funkcji z biblioteki DLL według numeru porządkowego a nie nazwy](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [Określić, której metody eksportowania użyjesz](../build/determining-which-exporting-method-to-use.md)

- [Określić, której metody łączenia użyjesz](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [Zainicjuj bibliotekę DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Importowanie do aplikacji](../build/importing-into-an-application.md)

- [Importowanie i eksportowanie funkcji śródwierszowych](../build/importing-and-exporting-inline-functions.md)

- [Importy wzajemne](../build/mutual-imports.md)

## <a name="see-also"></a>Zobacz też

[Importowanie i eksportowanie](../build/importing-and-exporting.md)