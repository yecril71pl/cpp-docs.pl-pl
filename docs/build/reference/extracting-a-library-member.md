---
title: "Wyodrębnianie członka biblioteki | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Lib
dev_langs: C++
helpviewer_keywords:
- LIB [C++], extracting library members
- EXTRACT library manager option
- libraries, extracting members
- -EXTRACT library manager option
- extracting library members
- /EXTRACT library manager option
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1c27e5c78316ec48d114bfd1715eb5874772a732
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="extracting-a-library-member"></a>Wyodrębnianie członka biblioteki
LIB można użyć do utworzenia pliku obiektu (.obj), który zawiera kopię członkiem istniejącej biblioteki. Aby wyodrębnić kopii elementu członkowskiego, użyj następującej składni:  
  
```  
LIB library /EXTRACT:member /OUT:objectfile  
```  
  
 To polecenie tworzy plik obj. wywołana *objectfile* zawierający kopię `member` z *biblioteki*. `member` Nazwa jest uwzględniana wielkość liter. Można wyodrębnić tylko jeden element członkowski za pomocą jednego polecenia. Opcja/out jest wymagana; nie została żadna nazwa wyjściowego domyślne. Jeśli plik o nazwie *objectfile* już istnieje w określonym katalogu (lub bieżącego katalogu, jeśli nie określono katalogu z *objectfile*), wyodrębnionego *objectfile*zastępuje istniejący plik.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki LIB](../../build/reference/lib-reference.md)