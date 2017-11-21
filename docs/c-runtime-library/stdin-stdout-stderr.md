---
title: stdin, stdout, stderr | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdin
- stderr
- stdout
dev_langs: C++
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8350cb0cea07298eefb9b3aa54b69a5b9d786d88
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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