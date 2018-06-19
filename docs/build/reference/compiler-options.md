---
title: Opcje kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler
- x86 Visual C++ compiler
- ARM Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bea07361a292ee5e7cde99cedad2d5ac4c8a53aa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374280"
---
# <a name="compiler-options"></a>Opcje kompilatora

Cl.exe to narzędzie, które kontroluje Microsoft Visual C++ (MSVC) C i C++ kompilatory i konsolidatora. Cl.exe można uruchomić tylko w systemach operacyjnych, które obsługuje program Microsoft Visual Studio dla systemu Windows.

> [!NOTE]  
> To narzędzie można uruchomić tylko z wiersza polecenia programu Visual Studio developer. Nie można uruchomić go z wiersza polecenia systemu lub z Eksploratora plików. Aby uzyskać więcej informacji, zobacz [kodu kompilacji C/C++ w wierszu polecenia](../building-on-the-command-line.md).

Kompilatory tworzenia plików obiektu (.obj) Format wspólnej pliku obiektu (COFF). Konsolidator tworzy pliki wykonywalne (.exe) lub biblioteki dołączanej (dynamicznie dll).

Należy pamiętać, że wszystkie opcje kompilatora jest uwzględniana wielkość liter. Możesz użyć kreski ułamkowej (`/`) lub kreska (`-`) można określić opcję kompilatora.

Aby skompilować bez konsolidacji, należy użyć [/c](../../build/reference/c-compile-without-linking.md) opcji.

## <a name="find-a-compiler-option"></a>Znajdź opcję kompilatora

Aby znaleźć opcję kompilatora określonego, zobacz jedną z następujących list:

- [Opcje kompilatora w porządku alfabetycznym](../../build/reference/compiler-options-listed-alphabetically.md)

- [Opcje kompilatora w rozbiciu na kategorie](../../build/reference/compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>Określ opcje kompilatora

Temat dla każdej opcji kompilatora opisano, jak można ją ustawić w środowisku programistycznym. Informacje dotyczące określania opcji poza Środowisko deweloperskie zobacz:

- [Składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md)

- [Pliki poleceń CL](../../build/reference/cl-command-files.md)

- [Zmienne środowiskowe CL](../../build/reference/cl-environment-variables.md)

## <a name="related-build-tools"></a>Narzędzia kompilacji pokrewne

[Opcje konsolidatora](../../build/reference/linker-options.md) wpłynąć na sposób składa się z programem.

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](../../build/reference/c-cpp-building-reference.md)  
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)  
[Szybka kompilacja](../../build/reference/fast-compilation.md)  
[CL wywołuje konsolidator](../../build/reference/cl-invokes-the-linker.md)  
