---
title: Składnia wiersza polecenia kompilatora MSVC
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 5cee76d5c053dbcfef33a191dc38a958338e4a82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294346"
---
# <a name="compiler-command-line-syntax"></a>Składnia wiersza polecenia kompilatora

W wierszu polecenia CL używa następującej składni:

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

W poniższej tabeli opisano dane wejściowe polecenia CL.

|Wpis|Znaczenie|
|-----------|-------------|
|*Opcja*|Co najmniej jeden [opcji CL](compiler-options.md). Należy pamiętać, że wszystkie opcje mają zastosowanie do wszystkich plików określonego źródła. Opcje są określone przez ukośnika (/) lub minus (-). Jeśli opcja przyjmuje argument, a opcja opis dokumentów czy spacji między opcją a argumenty. Nazwy opcji (z wyjątkiem opcji/Help) jest uwzględniana wielkość liter. Zobacz [kolejność opcji CL](order-of-cl-options.md) Aby uzyskać więcej informacji.|
|`file`|Nazwę jednego lub więcej plików źródłowych, pliki .obj lub biblioteki. CL kompiluje pliki źródłowe i przekazuje nazwy plików .obj i biblioteki do konsolidatora. Zobacz [Składnia nazwy pliku CL](cl-filename-syntax.md) Aby uzyskać więcej informacji.|
|*lib*|Jeden lub więcej nazw bibliotek. CL przekazuje te nazwy do konsolidatora.|
|*command-file*|Plik, który zawiera wiele opcji i nazw plików. Zobacz [pliki poleceń CL](cl-command-files.md) Aby uzyskać więcej informacji.|
|*zoptymalizowany pod kątem linku*|Co najmniej jeden [opcje konsolidatora MSVC](linker-options.md). CL przekazuje te opcje do konsolidatora.|

Można określić dowolną liczbę opcji, nazw plików i nazw bibliotek, tak długo, jak liczba znaków w wierszu polecenia nie przekracza 1024, limit definiowane przez system operacyjny.

Aby uzyskać informacje o wartości zwracanej przez cl.exe, zobacz [zwracają wartość zwracania cl.exe](return-value-of-cl-exe.md) .

> [!NOTE]
>  Limit danych wejściowych wiersza polecenia 1024 znaków nie gwarantuje pozostają bez zmian w przyszłych wydaniach systemu Windows.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)
