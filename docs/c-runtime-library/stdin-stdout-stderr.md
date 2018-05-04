---
title: stdin, stdout, stderr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- stdin
- stderr
- stdout
dev_langs:
- C++
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0f6226a6e38326a39ce2921e2a0d6219d01f005b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="stdin-stdout-stderr"></a>stdin, stdout, stderr
## <a name="syntax"></a>Składnia  
  
```  
  
      FILE *stdin;   
FILE *stdout;   
FILE *stderr;   
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Uwagi  
 Są to standardowe strumieni danych wejściowych, wyjściowych i błędów wyjścia.  
  
 Domyślnie standardowe dane wejściowe są odczytywane z klawiatury, gdy wyjście standardowe i błąd standardowy są drukowane na ekranie.  
  
 Następujące wskaźniki strumienia są umożliwiających dostęp do strumieni standardowe:  
  
|Wskaźnik|Strumień|  
|-------------|------------|  
|`stdin`|Standardowe dane wejściowe|  
|**STDOUT**|Standardowe dane wyjściowe|  
|`stderr`|Błąd standardowy|  
  
 Te wskaźniki może służyć jako argumenty do funkcji. Niektóre funkcje, takie jak **getchar** i `putchar`, użyj `stdin` i **stdout** automatycznie.  
  
 Te wskaźniki są stałe i nie można przypisać nowe wartości. `freopen` Funkcja może służyć do przekierowania strumieni plików na dysku lub innych urządzeń. System operacyjny umożliwia przekierowanie standardowe dane wejściowe i wyjściowe na poziomie polecenia programu.  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../c-runtime-library/stream-i-o.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)