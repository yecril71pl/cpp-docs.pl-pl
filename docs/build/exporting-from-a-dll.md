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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196745"
---
# <a name="exporting-from-a-dll"></a>Eksportowanie z biblioteki DLL

Plik DLL ma układ bardzo podobny do pliku. exe, z jedną ważną różnicą — plik DLL zawiera tabelę eksportów. Tabela eksportów zawiera nazwę każdej funkcji, którą Biblioteka DLL eksportuje do innych plików wykonywalnych. Te funkcje są punktami wejścia do biblioteki DLL; tylko funkcje w tabeli eksporty mogą być dostępne w innych plikach wykonywalnych. Wszystkie inne funkcje w bibliotece DLL są prywatne z biblioteką DLL. Tabelę eksportów biblioteki DLL można wyświetlić przy użyciu narzędzia [polecenia DUMPBIN](reference/dumpbin-reference.md) z opcją/Exports.

Można eksportować funkcje z biblioteki DLL przy użyciu dwóch metod:

- Utwórz plik definicji modułu (. def) i użyj pliku. def podczas kompilowania biblioteki DLL. Użyj tej metody, jeśli chcesz [eksportować funkcje z biblioteki DLL według liczby porządkowej, a nie nazwy](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

- Użyj słowa kluczowego **__declspec (dllexport)** w definicji funkcji.

Podczas eksportowania funkcji przy użyciu dowolnej metody upewnij się, że użyto konwencji wywoływania [__stdcall](../cpp/stdcall.md) .

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL za pomocą plików. def](exporting-from-a-dll-using-def-files.md)

- [Eksportowanie z biblioteki DLL przy użyciu __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Eksportowanie funkcji języka C++ do użycia w plikach wykonywalnych języka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Eksportowanie funkcji C do użycia w plikach wykonywalnych języka C lub C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Eksportowanie funkcji z biblioteki DLL według liczby porządkowej zamiast nazwy](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)

- [Określanie, której metody eksportowania użyć](determining-which-exporting-method-to-use.md)

- [Łączenie pliku wykonywalnego z biblioteką DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

- [Inicjowanie biblioteki DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Importowanie do aplikacji](importing-into-an-application.md)

- [Importowanie i eksportowanie funkcji śródwierszowych](importing-and-exporting-inline-functions.md)

- [Importy wzajemne](mutual-imports.md)

## <a name="see-also"></a>Zobacz też

[Importowanie i eksportowanie](importing-and-exporting.md)
