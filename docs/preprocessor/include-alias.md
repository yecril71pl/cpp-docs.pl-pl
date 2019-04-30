---
title: include_alias
ms.date: 12/16/2018
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
ms.openlocfilehash: 187fa94f7c2a5457df655081b87a7f49d38adfa2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384045"
---
# <a name="includealias"></a>include_alias

Określa, że w przypadku *alias_filename* znajduje się w `#include` zastępuje dyrektywy, kompilator *actual_filename* w tym miejscu.

## <a name="syntax"></a>Składnia

> #<a name="pragma-includealiasaliasfilename-actualfilename"></a>pragma include_alias ("*alias_filename*","*actual_filename*")
> #<a name="pragma-includealiasaliasfilename-actualfilename"></a>pragma include_alias (\<*alias_filename*>, \< *actual_filename*>)

## <a name="remarks"></a>Uwagi

**Include_alias** dyrektywa pragmy pozwala zastąpić pliki, które mają różne nazwy lub ścieżki do nazwy pliku dołączane przez pliki źródłowe. Na przykład niektóre systemy plików umożliwiają dłuższe nazwy plików nagłówkowych niż limit 8.3 systemu plików FAT. Kompilator nie może po prostu obciąć dłuższej nazwy do 8.3, ponieważ pierwsze osiem znaków dłuższej nazwy plików nagłówkowych nie musi być unikatowe. Gdy kompilator napotka *alias_filename* ciągu, zastępuje *actual_filename*, a szuka pliku nagłówka *actual_filename* zamiast tego. Ta pragma musi pojawić się przed odpowiednimi dyrektywami `#include`. Na przykład:

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

Poszukiwany alias musi odpowiadać specyfikacji, zarówno w wielkości liter jak i pisowni oraz użyciu znaków podwójnego cudzysłowu lub nawiasów ostrokątnych. **Include_alias** wykonuje proste dopasowanie na nazwy plików ciągów; odbywa się nie weryfikacji nazwy pliku. Na przykład, biorąc pod uwagę następujące dyrektywy,

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

aliasing (podstawienie) nie jest wykonywany, ponieważ ciągi pliku nagłówkowego nie są dokładnie zgodne. Ponadto nazwy plików nagłówkowych używane jako argumenty `/Yu` i `/Yc` opcje kompilatora lub `hdrstop` pragma, nie są zastępowane. Na przykład, jeśli plik z kodem źródłowym zawiera następujące dyrektywy,

```cpp
#include <AppleSystemHeaderStop.h>
```

odpowiadające opcje kompilatora to

> /YcAppleSystemHeaderStop.h

Możesz użyć **include_alias** pragmy do mapowania dowolnej nazwy pliku nagłówkowego. Na przykład:

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

Nie należy mieszać nazw plików ujętych w znaki cudzysłowu z nazwami plików ujętymi w nawiasy ostre. Na przykład dla dwóch podanych wyżej `#pragma include_alias` dyrektyw, kompilator nie wykona podstawienia dla następujących `#include` dyrektywy:

```cpp
#include <api.h>
#include "stdio.h"
```

Ponadto, następująca dyrektywa generuje błąd:

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

Należy pamiętać, że nazwa pliku zgłaszana w komunikatach o błędach lub jako wartość wstępnie zdefiniowanego `__FILE__` makro, to nazwa pliku, po wykonaniu podstawienia. Na przykład wyświetlić dane wyjściowe po następujących dyrektywach:

```cpp
#pragma include_alias( "VERYLONGFILENAME.H", "myfile.h" )
#include "VERYLONGFILENAME.H"
```

Błąd w VERYLONGFILENAME. H generuje następujący komunikat o błędzie:

```Output
myfile.h(15) : error C2059 : syntax error
```

Należy również zauważyć, że przechodniość nie jest obsługiwana. Biorąc pod uwagę następujące dyrektywy,

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

Kompilator wyszuka plik two.h zamiast three.h.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
