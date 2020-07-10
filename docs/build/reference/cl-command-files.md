---
title: Pliki poleceń CL
description: Kompilator MSVC umożliwia określenie plików poleceń, które zawierają opcje wiersza polecenia.
ms.date: 07/08/2020
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: 6deab4b11dcc6c53beb5b4fa8b014a56020c3420
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180945"
---
# <a name="cl-command-files"></a>Pliki poleceń CL

Plik poleceń to plik tekstowy, który zawiera opcje kompilatora i nazwy plików. Udostępnia opcje, które można w przeciwnym razie wpisać w [wierszu polecenia](compiler-command-line-syntax.md)lub określić przy użyciu [zmiennej środowiskowej CL](cl-environment-variables.md). CL akceptuje plik poleceń kompilatora jako argument, w zmiennej środowiskowej CL lub w wierszu polecenia. W przeciwieństwie do wiersza polecenia lub zmiennej środowiskowej CL, można użyć wielu wierszy opcji i nazw plików w pliku poleceń.

Opcje i nazwy plików w pliku poleceń są przetwarzane, gdy nazwa pliku polecenia pojawia się w zmiennej środowiskowej CL lub w wierszu polecenia. Jeśli jednak ta **`/link`** opcja pojawia się w pliku polecenia, wszystkie opcje w pozostałej części wiersza są przesyłane do konsolidatora. Opcje w późniejszych wierszach w pliku poleceń i opcje w wierszu polecenia po wywołaniu pliku polecenia są nadal akceptowane jako opcje kompilatora. Aby uzyskać więcej informacji na temat sposobu, w jaki kolejność opcji ma wpływ na ich interpretację, zobacz [kolejność CL](order-of-cl-options.md).

Plik polecenia nie może zawierać CL polecenie. Każda opcja musi rozpoczynać się i kończyć w tym samym wierszu; nie można użyć ukośnika odwrotnego ( **`\`** ), aby połączyć opcję w dwóch wierszach.

Plik poleceń jest określany za pomocą znaku ( **`@`** ), po którym następuje nazwa pliku. Nazwa pliku może określać ścieżkę bezwzględną lub względną.

Na przykład, jeśli następujące polecenie znajduje się w pliku o nazwie centr:

```cmd
/Ot /link LIBC.LIB
```

i należy określić następujące CL polecenia:

```cmd
CL /Ob2 @RESP MYAPP.C
```

polecenie do CL jest następujące:

```cmd
CL /Ob2 /Ot MYAPP.C /link LIBC.LIB
```

W tym miejscu możesz zobaczyć, w jaki sposób wiersz polecenia i polecenia dotyczące pliku poleceń są efektywnie połączone.

## <a name="see-also"></a>Zobacz też

[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)
