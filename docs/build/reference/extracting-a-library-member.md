---
title: Wyodrębnianie członka biblioteki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0dc0dc67a6d9e4a3ff61aa3b82ac10b9eabcb94b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="extracting-a-library-member"></a>Wyodrębnianie członka biblioteki
LIB można użyć do utworzenia pliku obiektu (.obj), który zawiera kopię członkiem istniejącej biblioteki. Aby wyodrębnić kopii elementu członkowskiego, użyj następującej składni:  
  
```  
LIB library /EXTRACT:member /OUT:objectfile  
```  
  
 To polecenie tworzy plik obj. wywołana *objectfile* zawierający kopię `member` z *biblioteki*. `member` Nazwa jest uwzględniana wielkość liter. Można wyodrębnić tylko jeden element członkowski za pomocą jednego polecenia. Opcja/out jest wymagana; nie została żadna nazwa wyjściowego domyślne. Jeśli plik o nazwie *objectfile* już istnieje w określonym katalogu (lub bieżącego katalogu, jeśli nie określono katalogu z *objectfile*), wyodrębnionego *objectfile*zastępuje istniejący plik.  
  
## <a name="see-also"></a>Zobacz też  
 [LIB — dokumentacja](../../build/reference/lib-reference.md)