---
title: Opcje kompilatora MSVC
ms.date: 01/29/2018
helpviewer_keywords:
- cl.exe compiler
- x86 MSVC compiler
- ARM MSVC compiler
- compiler options, C++
- x64 MSVC compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
ms.openlocfilehash: 831aade72cd728ec42aee5ef1f320deb7bdf173d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294268"
---
# <a name="compiler-options"></a>Opcje kompilatora

Cl.exe jest narzędziem, które kontroluje programu Microsoft Visual C++ (MSVC) C i Kompilatory języka C++ i konsolidatora. Cl.exe można uruchomić tylko w systemach operacyjnych, które obsługują program Microsoft Visual Studio for Windows.

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
