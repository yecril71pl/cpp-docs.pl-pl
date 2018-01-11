---
title: "Tryb tłumaczenia — stałe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
dev_langs: C++
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d1153251c08d626d17e87b5cc58dbd9360a21309
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="translation-mode-constants"></a>Tryb tłumaczenia — Stałe
## <a name="syntax"></a>Składnia  
  
```  
  
#include <fcntl.h>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 `_O_BINARY` i `_O_TEXT` manifestu stałe określić tryb tłumaczenia dla plików (`_open` i `_sopen`) lub tryb tłumaczenia dla strumieni (`_setmode`).  
  
 Dozwolone wartości to:  
  
 `_O_TEXT`  
 Otwiera plik w trybie tekstowym (translacji). Powrotu karetki - kombinacji wysuwu wiersza (CR LF) są przekształcane na jednym wysuwu wiersza (LF) na dane wejściowe. Znaki wysuwu wiersza są przetłumaczyć kombinacje CR LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako plik końcowy znak wejściowy. W plikach otwarty do odczytu i odczytu/zapisu `fopen` wyszukuje klawisze CTRL + Z końcem pliku i usuwa go, jeśli to możliwe. Odbywa się, ponieważ używa `fseek` i `ftell` funkcji Przenieś kończąc CTRL + Z pliku może spowodować `fseek` będzie działać nieprawidłowo zbliża się koniec pliku.  
  
 `_O_BINARY`  
 Otwiera plik w trybie binarnym (niezrozumiały). Powyżej tłumaczenia są pomijane.  
  
 `_O_RAW`  
 Taki sam jak `_O_BINARY`. Obsługiwane w przypadku zgodności C 2.0.  
  
 Aby uzyskać więcej informacji, zobacz [tekstu i we/wy binarne trybu pliku](../c-runtime-library/text-and-binary-mode-file-i-o.md) i [tłumaczenia pliku](../c-runtime-library/file-translation-constants.md).  
  
## <a name="see-also"></a>Zobacz też  
 [_otwórz, _wopen —](../c-runtime-library/reference/open-wopen.md)   
 [_pipe —](../c-runtime-library/reference/pipe.md)   
 [_sopen —, _wsopen —](../c-runtime-library/reference/sopen-wsopen.md)   
 [_setmode —](../c-runtime-library/reference/setmode.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)