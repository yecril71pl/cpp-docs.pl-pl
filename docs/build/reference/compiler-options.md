---
title: Opcje kompilatora
ms.date: 01/29/2018
helpviewer_keywords:
- cl.exe compiler
- x86 Visual C++ compiler
- ARM Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
ms.openlocfilehash: 8b887b2b9da6f38cdc1cf7287a69bbad8e88b989
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583888"
---
# <a name="compiler-options"></a>Opcje kompilatora

Cl.exe jest narzędziem, które kontroluje programu Microsoft Visual C++ (MSVC) C i Kompilatory języka C++ i konsolidatora. Cl.exe można uruchomić tylko w systemach operacyjnych, które obsługują program Microsoft Visual Studio for Windows.

> [!NOTE]
> To narzędzie można uruchomić tylko z poziomu wiersza polecenia dla deweloperów programu Visual Studio. Nie można uruchomić go z wiersza poleceń systemu lub Eksploratora plików. Aby uzyskać więcej informacji, zobacz [kodu kompilacji C/C++ w wierszu polecenia](../building-on-the-command-line.md).

Kompilatory generuje plikach obiektowych (.obj) Common Object File Format (COFF). Program łączący tworzy pliki wykonywalne (.exe) lub biblioteki dołączane dynamicznie (dll).

Należy pamiętać, że wszystkie opcje kompilatora są z uwzględnieniem wielkości liter. Może używać kreski ułamkowej (`/`) lub znak łącznika (`-`) można określić opcję kompilatora.

Aby skompilować bez łączenia, użyj [/c](../../build/reference/c-compile-without-linking.md) opcji.

## <a name="find-a-compiler-option"></a>Znajdź opcję kompilatora

Aby odnaleźć konkretną opcję kompilatora, zobacz jedną z następujących list:

- [Opcje kompilatora w porządku alfabetycznym](../../build/reference/compiler-options-listed-alphabetically.md)

- [Opcje kompilatora w rozbiciu na kategorie](../../build/reference/compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>Określ opcje kompilatora

Temat dla każdej opcji kompilatora omawia jak je ustawić w środowisku programistycznym. Aby uzyskać informacje dotyczące opcji określania poza środowiskiem programowania zobacz:

- [Składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md)

- [Pliki poleceń CL](../../build/reference/cl-command-files.md)

- [Zmienne środowiskowe CL](../../build/reference/cl-environment-variables.md)

## <a name="related-build-tools"></a>Narzędzia powiązanych kompilacji

[Opcje konsolidatora](../../build/reference/linker-options.md) również mieć wpływ na sposób kompilacji programu użytkownika.

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Szybka kompilacja](../../build/reference/fast-compilation.md)<br/>
[CL wywołuje konsolidator](../../build/reference/cl-invokes-the-linker.md)
