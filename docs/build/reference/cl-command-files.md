---
title: Pliki poleceń CL
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 1dc2d6bffe4d0681a04b875383215a0bbfc1a720
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440264"
---
# <a name="cl-command-files"></a>Pliki poleceń CL

Plik poleceń to plik tekstowy, który zawiera opcje i nazwy plików, które w przeciwnym razie można wpisać w [wierszu polecenia](compiler-command-line-syntax.md) lub określić przy użyciu [zmiennej środowiskowej CL](cl-environment-variables.md). CL akceptuje plik poleceń kompilatora jako argument w zmiennej środowiskowej CL lub w wierszu polecenia. W przeciwieństwie do wiersza polecenia lub zmiennej środowiskowej CL, plik poleceń pozwala na używanie wielu wierszy opcji i nazw plików.

Opcje i nazwy plików w pliku poleceń są przetwarzane zgodnie z lokalizacją pliku poleceń w zmiennej środowiskowej CL lub w wierszu polecenia. Jeśli jednak w pliku poleceń zostanie wyświetlona opcja/link, wszystkie opcje w pozostałej części wiersza są przesyłane do konsolidatora. Opcje w kolejnych wierszach w pliku poleceń i opcjach w wierszu polecenia po wywołaniu pliku polecenia są nadal akceptowane jako opcje kompilatora. Aby uzyskać więcej informacji na temat sposobu, w jaki kolejność opcji ma wpływ na ich interpretację, zobacz [kolejność CL](order-of-cl-options.md).

Plik polecenia nie może zawierać CL polecenie. Każda opcja musi rozpoczynać się i kończyć w tym samym wierszu; nie można użyć ukośnika odwrotnego ( **\\** ), aby połączyć opcję w dwóch wierszach.

Plik poleceń jest określany za pomocą znaku ( **\@** ), po którym następuje nazwa pliku; Nazwa pliku może określać ścieżkę bezwzględną lub względną.

Na przykład, jeśli następujące polecenie znajduje się w pliku o nazwie centr:

```
/Og /link LIBC.LIB
```

i należy określić następujące CL polecenia:

```
CL /Ob2 @RESP MYAPP.C
```

polecenie do CL jest następujące:

```
CL /Ob2 /Og MYAPP.C /link LIBC.LIB
```

Należy zauważyć, że wiersz polecenia i polecenia związane z plikiem poleceń są efektywnie połączone.

## <a name="see-also"></a>Zobacz też

[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)
