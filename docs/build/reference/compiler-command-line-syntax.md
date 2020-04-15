---
title: Składnia wiersza polecenia kompilatora MSVC
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 6a56474b537d78a3d0bea8a74d9082007cd2e295
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320548"
---
# <a name="compiler-command-line-syntax"></a>Składnia wiersza polecenia kompilatora

Wiersz polecenia CL używa następującej składni:

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

W poniższej tabeli opisano dane wejściowe do polecenia CL.

|Wpis|Znaczenie|
|-----------|-------------|
|*Opcja*|Co najmniej jedna [opcja CL](compiler-options.md). Należy zauważyć, że wszystkie opcje dotyczą wszystkich określonych plików źródłowych. Opcje są określane przez ukośnik do przodu (/) lub myślnik (-). Jeśli opcja przyjmuje argument, opis opcji dokumentuje, czy odstęp jest dozwolony między opcją a argumentami. W nazwach opcji (z wyjątkiem opcji /HELP) rozróżniana jest wielkość liter. Aby uzyskać więcej informacji, zobacz [Kolejność opcji CL.](order-of-cl-options.md)|
|`file`|Nazwa jednego lub większej liczby plików źródłowych, plików obj lub bibliotek. CL kompiluje pliki źródłowe i przekazuje nazwy plików i bibliotek obj do konsolidatora. Aby uzyskać więcej informacji, zobacz [składnia nazwy pliku CL.](cl-filename-syntax.md)|
|*Lib*|Co najmniej jedna nazwa biblioteki. CL przekazuje te nazwy do konsolidatora.|
|*plik polecenia*|Plik zawierający wiele opcji i nazwy plików. Aby uzyskać więcej informacji, zobacz [Pliki poleceń CL.](cl-command-files.md)|
|*link-opt*|Co najmniej jedna [opcja konsolidatora MSVC](linker-options.md). CL przekazuje te opcje do konsolidatora.|

Można określić dowolną liczbę opcji, nazw plików i nazw bibliotek, o ile liczba znaków w wierszu polecenia nie przekracza 1024, limit podyktowany przez system operacyjny.

Aby uzyskać informacje o wartości zwracanej cl.exe, zobacz [Wartość zwracana cl.exe](return-value-of-cl-exe.md) .

> [!NOTE]
> Limit wejściowy wiersza polecenia wynoszący 1024 znaki nie jest gwarantowany, aby pozostał taki sam w przyszłych wersjach systemu Windows.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)
