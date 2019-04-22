---
title: hdrstop
ms.date: 11/04/2016
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
ms.openlocfilehash: 1590b5916a8d9c00b6e988bacc7cd857c29d6775
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035218"
---
# <a name="hdrstop"></a>hdrstop
Daje dodatkową kontrolę nad nazwami plików kompilacji wstępnej oraz nad lokalizacją, w której zapisywany jest stan kompilacji.

## <a name="syntax"></a>Składnia

```
#pragma hdrstop [( "filename" )]
```

## <a name="remarks"></a>Uwagi

*Filename* nazywa się prekompilowanego pliku nagłówkowego do użycia lub Utwórz (w zależności od tego, czy [/Yu](../build/reference/yu-use-precompiled-header-file.md) lub [/Yc](../build/reference/yc-create-precompiled-header-file.md) jest określony). Jeśli *filename* nie zawiera specyfikacji ścieżki prekompilowanego pliku nagłówkowego zakłada, że w tym samym katalogu co plik źródłowy.

Jeśli plik języka C lub C++ zawiera **hdrstop** pragma, gdy skompilowano z opcją `/Yc`, kompilator zapisuje stan kompilacji do lokalizacji pragmy. Nie jest zapisywany skompilowany stan dowolnego kodu, który następuje po pragmie.

Użyj *filename* nazwę pliku wstępnie skompilowanego nagłówka, w którym zostanie zapisany stan kompilacji. Odstęp między **hdrstop** i *filename* jest opcjonalne. Nazwa pliku określona w **hdrstop** pragma jest ciągiem i dlatego warunki ograniczające dowolny ciąg języka C lub C++. W szczególności, musisz ująć go w znaki cudzysłowu i używać znaku ucieczki (ukośnik odwrotny), aby określić nazwy katalogów. Na przykład:

```
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

Nazwa wstępnie skompilowanego pliku nagłówkowego jest określana zgodnie z następującymi regułami według pierwszeństwa:

1. Argument `/Fp` — opcja kompilatora

2. *Filename* argument `#pragma hdrstop`

3. Nazwa podstawowa pliku źródłowego z rozszerzeniem .PCH

Aby uzyskać `/Yc` i `/Yu` opcji, jeśli żadna z dwóch opcji kompilacji ani **hdrstop** pragma Określa nazwę pliku, nazwa podstawowa pliku źródłowego jest używana jako nazwa podstawowa pliku wstępnie skompilowanego nagłówka.

Możesz również użyć poleceń przetwarzania wstępnego, aby wykonać makro zastępujące w następujący sposób:

```
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

Decydują następujące reguły **hdrstop** umieszczenia pragmy:

- Musi znajdować się poza wszelkimi deklaracjami i definicjami danych lub funkcji.

- Musi być określona w pliku źródłowym, a nie w pliku nagłówkowym.

## <a name="example"></a>Przykład

```
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    ...                              // Some code to display string
}
#pragma hdrstop
```

W tym przykładzie **hdrstop** pragma pojawia się po dwa pliki zostały włączone i wbudowanej funkcji został zdefiniowany. Pozornie może wydawać się to dziwnym miejscem dla pragmy. Rozważmy jednak, że przy użyciu ręcznych opcji kompilacji wstępnej, `/Yc` i `/Yu`, za pomocą **hdrstop** pragma umożliwia wstępna kompilacja całych plików źródłowych — nawet kodu w tekście. Kompilator Microsoft nie ogranicza do kompilacji wstępnej tylko deklaracji danych.

## <a name="see-also"></a>Zobacz także

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)