---
title: Pliki definicji modułu (.Def)
ms.date: 11/04/2016
helpviewer_keywords:
- def files
- module definition files
- .def files
ms.assetid: 08c0bc28-c5d2-47aa-9624-7fc68bcaa4d8
ms.openlocfilehash: 0047f24722644cd9a68bbbf827ced26ad085d4c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321231"
---
# <a name="module-definition-def-files"></a>Pliki definicji modułu (.Def)

Pliki definicji modułu (.def) zapewniają konsolidatora z informacjami dotyczącymi eksportu, atrybuty i inne informacje o program ma być połączone. Plik .def jest najbardziej przydatne podczas tworzenia biblioteki DLL. Ponieważ istnieją [opcje konsolidatora MSVC](linker-options.md) które mogą być używane zamiast instrukcji definicji modułu .def — pliki nie są zwykle wymagane. Można również użyć [__declspec(dllexport)](../exporting-from-a-dll-using-declspec-dllexport.md) jako sposób określania wyeksportowanych funkcji.

Plik .def można wywołać w fazie konsolidatora z [/DEF (Określ plik definicji modułu)](def-specify-module-definition-file.md) — opcja konsolidatora.

Jeśli tworzysz plik .exe, który nie eksportuje żadnych danych, używając pliku .def spowoduje, że Twoje dane wyjściowe pliku większych i wolniejszych podczas ładowania.

Aby uzyskać przykład, zobacz [eksportowanie z biblioteki DLL przy użyciu DEF plików](../exporting-from-a-dll-using-def-files.md).

Zobacz następujące sekcje, aby uzyskać więcej informacji:

- [Zasady dla instrukcji definicji modułu](rules-for-module-definition-statements.md)

- [EXPORTS](exports.md)

- [HEAPSIZE](heapsize.md)

- [LIBRARY](library.md)

- [NAZWA](name-c-cpp.md)

- [SEKCJE](sections-c-cpp.md)

- [STACKSIZE](stacksize.md)

- [STUB](stub.md)

- [WERSJA](version-c-cpp.md)

- [Słowa zastrzeżone](reserved-words.md)

## <a name="see-also"></a>Zobacz także

[Dokumentacja kompilacji w języku C/C++](c-cpp-building-reference.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
