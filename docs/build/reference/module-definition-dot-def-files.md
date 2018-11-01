---
title: Pliki definicji modułu (.Def)
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: a882d71e76b961fefb7059bee8634507f12f7986
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460440"
---
# <a name="module-definition-def-files"></a>Pliki definicji modułu (.Def)

Pliki definicji modułu (.def) zapewniają konsolidatora z informacjami dotyczącymi eksportu, atrybuty i inne informacje o program ma być połączone. Plik .def jest najbardziej przydatne podczas tworzenia biblioteki DLL. Ponieważ istnieją [opcje konsolidatora](../../build/reference/linker-options.md) które mogą być używane zamiast instrukcji definicji modułu .def — pliki nie są zwykle wymagane. Można również użyć [__declspec(dllexport)](../../build/exporting-from-a-dll-using-declspec-dllexport.md) jako sposób określania wyeksportowanych funkcji.

Plik .def można wywołać w fazie konsolidatora z [/DEF (Określ plik definicji modułu)](../../build/reference/def-specify-module-definition-file.md) — opcja konsolidatora.

Jeśli tworzysz plik .exe, który nie eksportuje żadnych danych, używając pliku .def spowoduje, że Twoje dane wyjściowe pliku większych i wolniejszych podczas ładowania.

Aby uzyskać przykład, zobacz [eksportowanie z biblioteki DLL przy użyciu DEF plików](../../build/exporting-from-a-dll-using-def-files.md).

Zobacz następujące sekcje, aby uzyskać więcej informacji:

- [Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)

- [EXPORTS](../../build/reference/exports.md)

- [HEAPSIZE](../../build/reference/heapsize.md)

- [LIBRARY](../../build/reference/library.md)

- [NAZWA](../../build/reference/name-c-cpp.md)

- [SEKCJE](../../build/reference/sections-c-cpp.md)

- [STACKSIZE](../../build/reference/stacksize.md)

- [STUB](../../build/reference/stub.md)

- [WERSJA](../../build/reference/version-c-cpp.md)

- [Słowa zastrzeżone](../../build/reference/reserved-words.md)

## <a name="see-also"></a>Zobacz też

[Dokumentacja kompilacji w języku C/C++](../../build/reference/c-cpp-building-reference.md)<br/>
[Opcje konsolidatora](../../build/reference/linker-options.md)