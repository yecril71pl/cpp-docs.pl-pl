---
title: Opcje kompilatora MSVC
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler
- x86 MSVC compiler
- ARM MSVC compiler
- compiler options, C++
- x64 MSVC compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
ms.openlocfilehash: ab41a5de027f28b361937e58fb179fd72db54e4e
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221741"
---
# <a name="compiler-options"></a>Opcje kompilatora

Cl.exe jest narzędziem, które kontroluje Microsoft C++ (MSVC) C i C++ konsolidatora i Kompilatory języka. Cl.exe można uruchomić tylko w systemach operacyjnych, które obsługują program Microsoft Visual Studio for Windows.

> [!NOTE]
> To narzędzie można uruchomić tylko z poziomu wiersza polecenia dla deweloperów programu Visual Studio. Nie można uruchomić go z wiersza poleceń systemu lub Eksploratora plików. Aby uzyskać więcej informacji, zobacz [możesz używać zestawu narzędzi MSVC z wiersza polecenia](../building-on-the-command-line.md).

Kompilatory generuje plikach obiektowych (.obj) Common Object File Format (COFF). Program łączący tworzy pliki wykonywalne (.exe) lub biblioteki dołączane dynamicznie (dll).

Należy pamiętać, że wszystkie opcje kompilatora są z uwzględnieniem wielkości liter. Może używać kreski ułamkowej (`/`) lub znak łącznika (`-`) można określić opcję kompilatora.

Aby skompilować bez łączenia, użyj [/c](c-compile-without-linking.md) opcji.

## <a name="find-a-compiler-option"></a>Znajdź opcję kompilatora

Aby odnaleźć konkretną opcję kompilatora, zobacz jedną z następujących list:

- [Opcje kompilatora w porządku alfabetycznym](compiler-options-listed-alphabetically.md)

- [Opcje kompilatora w rozbiciu na kategorie](compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>Określ opcje kompilatora

Temat dla każdej opcji kompilatora omawia jak je ustawić w środowisku programistycznym. Aby uzyskać informacje dotyczące opcji określania poza środowiskiem programowania zobacz:

- [Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)

- [Pliki poleceń CL](cl-command-files.md)

- [Zmienne środowiskowe CL](cl-environment-variables.md)

## <a name="related-build-tools"></a>Narzędzia powiązanych kompilacji

[Opcje konsolidatora MSVC](linker-options.md) również mieć wpływ na sposób kompilacji programu użytkownika.

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](c-cpp-building-reference.md)<br/>
[CL wywołuje konsolidator](cl-invokes-the-linker.md)
