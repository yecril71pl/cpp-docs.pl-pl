---
title: hdrstop | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
dev_langs:
- C++
helpviewer_keywords:
- hdrstop pragma
- pragmas, hdrstop
ms.assetid: 5ea8370a-10d1-4538-ade6-4c841185da0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f1c628efaf45be87dcfc046cf1774c762c157f4f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="hdrstop"></a>hdrstop
Daje dodatkową kontrolę nad nazwami plików kompilacji wstępnej oraz nad lokalizacją, w której zapisywany jest stan kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma hdrstop [( "filename" )]    
```  
  
## <a name="remarks"></a>Uwagi  
 *Filename* jest nazwą prekompilowanego pliku nagłówkowego lub utworzeniu (w zależności od tego, czy [/Yu](../build/reference/yu-use-precompiled-header-file.md) lub [/Yc](../build/reference/yc-create-precompiled-header-file.md) jest określony). Jeśli *filename* nie zawiera określenia ścieżki prekompilowanego pliku nagłówkowego zakłada, że w tym samym katalogu co plik źródłowy.  
  
 Jeśli plik C lub C++ zawiera **hdrstop** pragma, gdy skompilowano z opcją /Yc, kompilator zapisuje stan kompilacji do lokalizacji pragma. Nie jest zapisywany skompilowany stan dowolnego kodu, który następuje po pragmie.  
  
 Użyj *filename* nazwę pliku prekompilowanego nagłówka, w którym jest zapisany stan skompilowany. Odstęp między **hdrstop** i *filename* jest opcjonalna. Nazwa pliku określona w **hdrstop** pragma jest ciągiem i w związku z tym podlega ograniczenia dowolnego ciągu języka C lub C++. W szczególności, musisz ująć go w znaki cudzysłowu i używać znaku ucieczki (ukośnik odwrotny), aby określić nazwy katalogów. Na przykład:  
  
```  
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )  
```  
  
 Nazwa wstępnie skompilowanego pliku nagłówkowego jest określana zgodnie z następującymi regułami według pierwszeństwa:  
  
1.  Argument do opcji kompilatora /Fp  
  
2.  *Filename* argumentu #**pragma hdrstop**  
  
3.  Nazwa podstawowa pliku źródłowego z rozszerzeniem .PCH  
  
 Dla opcji /Yc i /Yu, jeśli żadna z opcji kompilacji dwóch ani **hdrstop** pragma Określa nazwę pliku, podstawowa nazwa pliku źródłowego jest używana jako nazwę podstawową prekompilowanego pliku nagłówkowego.  
  
 Możesz również użyć poleceń przetwarzania wstępnego, aby wykonać makro zastępujące w następujący sposób:  
  
```  
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"  
#define PCH_FNAME "PROG.PCH"  
.  
.  
.  
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )  
```  
  
 Następujące zasady regulują where **hdrstop** pragma można umieścić:  
  
-   Musi znajdować się poza wszelkimi deklaracjami i definicjami danych lub funkcji.  
  
-   Musi być określona w pliku źródłowym, a nie w pliku nagłówkowym.  
  
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
  
 W tym przykładzie **hdrstop** pragma pojawia się po dwa pliki zostały włączone i zdefiniowano funkcję śródwierszową. Pozornie może wydawać się to dziwnym miejscem dla pragmy. Należy wziąć pod uwagę, jednak tego za pomocą ręcznej opcje wstępnej kompilacji, /Yc i /Yu, z **hdrstop** pragma sprawia, że można przeprowadzać prekompilowanie pliki źródłowe całego — nawet kodu wbudowanego. Kompilator Microsoft nie ogranicza do kompilacji wstępnej tylko deklaracji danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)