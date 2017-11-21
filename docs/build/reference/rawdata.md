---
title: -RAWDATA | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /rawdata
dev_langs: C++
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0a0d9517bae5bdd1eed6cfafda496643aee666d4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rawdata"></a>/RAWDATA
```  
/RAWDATA[:{1|2|4|8|NONE[,number]]  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja powoduje wyświetlenie nieprzetworzonej zawartości każdej sekcji w pliku. Argumenty kontrolować format wyświetlania, jak pokazano poniżej:  
  
|Argument|Wynik|  
|--------------|------------|  
|1|Domyślnie. Zawartość jest wyświetlana w bajty szesnastkowe, a także jako znaki ASCII, gdy mają reprezentację wydruku.|  
|2|Zawartość jest wyświetlana jako wartości szesnastkowe 2-bajtowych.|  
|4|Zawartość jest wyświetlana jako wartości szesnastkowe 4-bajtowych.|  
|8|Zawartość jest wyświetlana jako wartości szesnastkowe 8-bajtowych.|  
|BRAK|Nieprzetworzone dane są pomijane. Ten argument jest przydatne do kontroli danych wyjściowych/ALL.|  
|*Numer*|Wiersze są ustawione na szerokość, która przechowuje `number` wartości dla każdego wiersza.|  
  
 Tylko [/HEADERS](../../build/reference/headers.md) — opcja polecenia DUMPBIN jest dostępny do użytku na pliki tworzone z [/GL](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje DUMPBIN](../../build/reference/dumpbin-options.md)