---
title: include_alias, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
ms.openlocfilehash: aa3714186e8f95d4044ba5a3b2bc2d5fcfb1fc9c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218907"
---
# <a name="include_alias-pragma"></a>include_alias, pragma

Określa, że po znalezieniu *alias_filename* w `#include` dyrektywie, kompilator zastępuje *actual_filename* w miejscu.

## <a name="syntax"></a>Składnia

<!-- localization note - it's important to have the italic and bold characters immediately adjacent here. -->
> **#pragma include_alias (** "*alias_filename*" **,** "*actual_filename*" **)** \
> **#pragma include_alias (** \< *alias_filename*>  **,** *actual_filename*) \<> 

## <a name="remarks"></a>Uwagi

Dyrektywa pragma **include_alias** umożliwia zastępowanie plików o różnych nazwach lub ścieżkach nazw plików dołączonych do plików źródłowych. Na przykład niektóre systemy plików dopuszczają dłuższe nazwy plików nagłówkowe niż limit systemu plików 8,3 FAT. Kompilator nie może po prostu obciąć dłuższych nazw do 8,3, ponieważ pierwsze osiem znaków dłuższych nazw plików nagłówkowych może nie być unikatowe. Za każdym razem, gdy kompilator widzi ciąg alias_filename `#include` w dyrektywie, zastępuje nazwę *actual_filename* . Następnie ładuje plik nagłówkowy *actual_filename* . Ta pragma musi pojawić się przed odpowiednimi dyrektywami `#include`. Na przykład:

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

Alias do wyszukania musi być dokładnie zgodny ze specyfikacją. Wielkość liter, pisownia i użycie podwójny cudzysłów lub nawiasy ostre muszą być zgodne. **Include_alias** pragma jest prostym dopasowaniem ciągu do nazw plików. Nie jest przeprowadzana weryfikacja innych nazw plików. Na przykład, biorąc pod uwagę następujące dyrektywy,

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

nie jest wykonywane podstawianie aliasów, ponieważ ciągi pliku nagłówka nie są dokładnie zgodne. Ponadto nazwy plików nagłówków używane jako argumenty dla `/Yu` opcji `hdrstop` kompilatora i `/Yc` lub pragma nie są zastępowane. Na przykład, jeśli plik z kodem źródłowym zawiera następujące dyrektywy,

```cpp
#include <AppleSystemHeaderStop.h>
```

odpowiadające opcje kompilatora to

> **/YcAppleSystemHeaderStop.h**

Możesz użyć dyrektywy pragma **include_alias** , aby zmapować dowolną nazwę pliku nagłówkowego na inną. Przykład:

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

Nie mieszaj nazw plików ujętych w znaki podwójnego cudzysłowu z nazwami plików ujętych w nawiasy ostre. Na przykład, mając powyższe dwie `#pragma include_alias` dyrektywy, kompilator nie ma podstawienia w następujących `#include` dyrektywach:

```cpp
#include <api.h>
#include "stdio.h"
```

Ponadto, następująca dyrektywa generuje błąd:

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

Nazwa pliku raportowana w komunikatach o błędach lub jako wartość wstępnie `__FILE__` zdefiniowanego makra to po zakończeniu podstawienia. Na przykład, zobacz dane wyjściowe po następujących dyrektywach:

```cpp
#pragma include_alias( "VERYLONGFILENAME.H", "myfile.h" )
#include "VERYLONGFILENAME.H"
```

Błąd w *VERYLONGFILENAME. H* generuje następujący komunikat o błędzie:

```Output
myfile.h(15) : error C2059 : syntax error
```

Należy również zauważyć, że przechodniość nie jest obsługiwana. Biorąc pod uwagę następujące dyrektywy,

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

Kompilator wyszukuje plik *dwa. h* zamiast *trzy. h*.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
