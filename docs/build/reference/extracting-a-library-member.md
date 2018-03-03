---
title: "Wyodrębnianie członka biblioteki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 38f45463bb76f858d1b88c059de57a4b8b86227e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="extracting-a-library-member"></a>Wyodrębnianie członka biblioteki
LIB można użyć do utworzenia pliku obiektu (.obj), który zawiera kopię członkiem istniejącej biblioteki. Aby wyodrębnić kopii elementu członkowskiego, użyj następującej składni:  
  
```  
LIB library /EXTRACT:member /OUT:objectfile  
```  
  
 To polecenie tworzy plik obj. wywołana *objectfile* zawierający kopię `member` z *biblioteki*. `member` Nazwa jest uwzględniana wielkość liter. Można wyodrębnić tylko jeden element członkowski za pomocą jednego polecenia. Opcja/out jest wymagana; nie została żadna nazwa wyjściowego domyślne. Jeśli plik o nazwie *objectfile* już istnieje w określonym katalogu (lub bieżącego katalogu, jeśli nie określono katalogu z *objectfile*), wyodrębnionego *objectfile*zastępuje istniejący plik.  
  
## <a name="see-also"></a>Zobacz też  
 [LIB — dokumentacja](../../build/reference/lib-reference.md)