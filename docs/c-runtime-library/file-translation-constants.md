---
title: Stałe tłumaczenia pliku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.constants.file
dev_langs:
- C++
helpviewer_keywords:
- translation constants
- file translation [C++], constants
- translation, file translation constants
- translation, constants
- constants [C++], file translation mode
- file translation [C++]
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 881402933978f5fe714a9b1950a9eade01494c79
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="file-translation-constants"></a>Stałe tłumaczenia pliku
## <a name="syntax"></a>Składnia  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Uwagi  
 Te stałe Określ tryb tłumaczenia (**"b"** lub **"t"**). Tryb jest uwzględniona w parametrach określenie typu dostępu (**"r"**, **"w"**, **""**, **"r +"**, **"w +"**, **"+"**).  
  
 Tryby tłumaczenia są następujące:  
  
 **t**  
 Zostanie otwarty w trybie tekstowym (translacji). W tym trybie kombinacje (CR LF) karetki return/wysuw wiersza są przekształcane na pojedynczy znaki wysuwu wiersza (LF) na wejściu i LF znaki są tłumaczone na kombinacje CR LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako plik końcowy znak wejściowy. W plikach otwarty do odczytu lub odczytu/zapisu `fopen` wyszukuje klawisze CTRL + Z końcem pliku i usuwa go, jeśli to możliwe. Odbywa się, ponieważ używa `fseek` i `ftell` funkcji Przenieś kończąc CTRL + Z pliku może spowodować `fseek` będzie działać nieprawidłowo zbliża się koniec pliku.  
  
> [!NOTE]
>  **t** opcja nie jest częścią standardu ANSI `fopen` i `freopen`. Rozszerzenia Microsoft jest i nie powinna być używana których przenośność ANSI jest potrzebne.  
  
 **b**  
 Zostanie otwarty w trybie binarnym (niezrozumiały). Powyżej tłumaczenia są pomijane.  
  
 Jeśli **t** lub **b** nie została podana w *tryb*, tryb tłumaczenia jest definiowana za pomocą zmiennej domyślny tryb [_fmode —](../c-runtime-library/fmode.md). Aby uzyskać więcej informacji o używaniu trybach tekstowym i binarnym, zobacz [tekstu i we/wy binarne trybu pliku](../c-runtime-library/text-and-binary-mode-file-i-o.md).  
  
## <a name="see-also"></a>Zobacz też  
 [_fdopen —, _wfdopen —](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen —, _wfopen —](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen —, _wfreopen —](../c-runtime-library/reference/freopen-wfreopen.md)   
 [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)