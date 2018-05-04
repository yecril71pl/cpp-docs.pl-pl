---
title: Stałe dostępu do odczytu i zapisu pliku | Dokumentacja firmy Microsoft
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
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f57ac6ffc3c13c640d7bdf6a2ec64912148bfbc3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="file-readwrite-access-constants"></a>Odczyt/zapis pliku — Stałe dostępu
## <a name="syntax"></a>Składnia  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Uwagi  
 Te stałe Określ typ dostępu ("a", "r" lub "w") żądanego pliku. Zarówno [tryb tłumaczenia](../c-runtime-library/file-translation-constants.md) ("b" lub "t") i [tryb commit-to-disk](../c-runtime-library/commit-to-disk-constants.md) ("c" lub "n") można określić typu dostępu.  
  
 Poniżej opisano typy dostępu.  
  
 **""**  
 Zostanie otwarty do zapisu na końcu pliku (dołączanie); Tworzy plik, jeśli nie istnieje. Wszystkie zapisu operacje wykonywane na końcu pliku. Mimo że może być położenia wskaźnika pliku przy użyciu `fseek` lub **rewind**, on jest zawsze przeniesiony z powrotem do koniec pliku przed żadnego zapisu, wykonywane są wymienione.  
  
 **"+"**  
 Takie same jak powyżej, ale również umożliwia odczyt.  
  
 **"r"**  
 Zostanie otwarty do odczytu. Jeśli plik nie istnieje lub nie można odnaleźć, wywołania do otwierania pliku zakończy się niepowodzeniem.  
  
 **"r +"**  
 Otwiera odczytywanie i zapisywanie. Jeśli plik nie istnieje lub nie można odnaleźć, wywołania do otwierania pliku zakończy się niepowodzeniem.  
  
 **"w"**  
 Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaną zniszczone.  
  
 **"w +"**  
 Otwiera pusty plik na odczytywanie i zapisywanie. Jeśli dany plik istnieje, jego zawartość zostaną zniszczone.  
  
 Jeśli określono "r +", "w +" lub "+" typ, odczytywanie i zapisywanie są dozwolone (plik jest określany jako otwarte dla "update"). Jednak podczas przełączania się między odczytu i zapisu, musi być aktywne `fflush`, `fsetpos`, `fseek`, lub **rewind** operacji. Bieżąca pozycja można określić dla `fsetpos` lub `fseek` operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [_fdopen —, _wfdopen —](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen —, _wfopen —](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen —, _wfreopen —](../c-runtime-library/reference/freopen-wfreopen.md)   
 [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [_popen —, _wpopen —](../c-runtime-library/reference/popen-wpopen.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)