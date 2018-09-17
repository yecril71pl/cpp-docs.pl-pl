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
ms.openlocfilehash: cc0b7c9a2d8707d8a1939a47d4fae2ec896e4d2b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700533"
---
# <a name="file-readwrite-access-constants"></a>Odczyt/zapis pliku — Stałe dostępu
## <a name="syntax"></a>Składnia  
  
```  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Uwagi  

Te stałe Określ typ dostępu ("a", "r" lub "t"), wnioskowany dla pliku. Zarówno [tryb translacji](../c-runtime-library/file-translation-constants.md) ("b" lub "t") i [tryb commit-to-disk](../c-runtime-library/commit-to-disk-constants.md) ("c" lub "n") można określić za pomocą typu dostępu.  
  
W tej tabeli opisano typy dostępu:  

|Typ dostępu|Opis|
|----------|----------------|
|**"r"**|Otwiera do odczytu. Jeśli plik nie istnieje lub nie można znaleźć, wywołanie do otwierania pliku kończy się niepowodzeniem.|
|**"w"**|Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona.|
|**""**|Zostanie otwarty do zapisu na końcu pliku (dołączanie); najpierw tworzy plik, jeśli nie istnieje. Zapisu wszystkie operacje są wykonywane na końcu pliku. Mimo że wskaźnik pliku może być przeniesiony za pomocą `fseek` lub `rewind`, on jest zawsze przenoszony z powrotem na koniec pliku przed wszelkie zapisu operacji jest przeprowadzane. |
|**"r +"**|Otwiera Odczyt i zapis. Jeśli plik nie istnieje lub nie można znaleźć, wywołanie do otwierania pliku kończy się niepowodzeniem.|
|**"w +"**|Otwiera pusty plik Odczyt i zapis. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona.|
|**"+"**|Taka sama jak **""** , ale również umożliwia odczyt.|

Jeśli "r +", "w +" lub "+" typ jest określony, będą miały Odczyt i zapis (plik jest określany jako otwarty do "aktualizacji"). Jednak podczas przełączania się między Odczyt i zapis, musi istnieć interwencyjne `fflush`, `fsetpos`, `fseek`, lub `rewind` operacji. Bieżąca pozycja może być określona dla `fsetpos` lub `fseek` operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [_fdopen —, _wfdopen —](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen —, _wfopen —](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen —, _wfreopen —](../c-runtime-library/reference/freopen-wfreopen.md)   
 [_fsopen —, _wfsopen —](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [_popen —, _wpopen —](../c-runtime-library/reference/popen-wpopen.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)