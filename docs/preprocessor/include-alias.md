---
title: include_alias | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b03ec43ff213e330c88886fb485c0e18700c8a86
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="includealias"></a>include_alias

Określa, że *short_filename* ma być używany jako alias *long_filename*.

## <a name="syntax"></a>Składnia

> #<a name="pragma-includealiaslongfilename-shortfilename"></a>pragma include_alias ("*long_filename*","*short_filename*")  
> #<a name="pragma-includealiaslongfilename-shortfilename"></a>pragma include_alias (*long_filename*, *short_filename*)

## <a name="remarks"></a>Uwagi

Niektóre systemy plików umożliwiają dłuższe nazwy plików nagłówków niż limit 8.3 systemu plików FAT. Kompilator nie może po prostu obciąć dłuższej nazwy do 8.3, ponieważ pierwsze osiem znaków dłuższej nazwy plików nagłówka nie musi być unikatowe. Zawsze, gdy wystąpi kompilator *long_filename* ciągu zastępuje *short_filename*oraz szuka pliku nagłówka *short_filename* zamiast tego. Ta pragma musi pojawić się przed odpowiednimi dyrektywami `#include`. Na przykład:

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

Poszukiwany alias musi odpowiadać specyfikacji, zarówno w wielkości liter jak i pisowni oraz użyciu znaków podwójnego cudzysłowu lub nawiasów ostrokątnych. **Include_alias** pragma wykonuje prostego ciągu na nazwy plików; Weryfikacja nie innych filename jest przeprowadzana. Na przykład, biorąc pod uwagę następujące dyrektywy,

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

aliasing (podstawienie) nie jest wykonywany, ponieważ ciągi pliku nagłówka nie są dokładnie zgodne. Ponadto nagłówka nazw plików używane jako argumenty opcji kompilatora /Yu i /Yc lub **hdrstop** pragma, nie są zastępowane. Na przykład, jeśli plik z kodem źródłowym zawiera następujące dyrektywy,
  
```cpp
#include <AppleSystemHeaderStop.h>
```

odpowiadające opcje kompilatora to

> /YcAppleSystemHeaderStop.h

Można użyć **include_alias** pragma do mapowania nazwy pliku nagłówka. Na przykład:

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

Nie należy mieszać nazw plików ujętych w znaki cudzysłowu z nazwami plików ujętymi w nawiasy ostre. Na przykład podane powyżej dwa **#pragma include_alias** dyrektywy, kompilator wykonuje podstawienie nie na następujących `#include` dyrektywy:

```cpp
#include <api.h>
#include "stdio.h"
```

Ponadto, następująca dyrektywa generuje błąd:

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

Pamiętaj, że nazwa pliku jest zgłaszany w komunikatach o błędach lub jako wartość wstępnie zdefiniowane **&#95; &#95; Plik &#95; &#95;**  makra jest nazwa pliku po podstawienie została wykonana. Na przykład wyświetlić dane wyjściowe po następujące dyrektywy:

```cpp
#pragma include_alias( "VeryLongFileName.H", "myfile.h" )
#include "VeryLongFileName.H"
```

Wystąpił błąd w VERYLONGFILENAME. H tworzy komunikat o błędzie:

```Output
myfile.h(15) : error C2059 : syntax error
```

Należy również zauważyć, że przechodniość nie jest obsługiwana. Biorąc pod uwagę następujące dyrektywy,

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

kompilator wyszuka plik TWO.H zamiast THREE.H.  

## <a name="see-also"></a>Zobacz też

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)