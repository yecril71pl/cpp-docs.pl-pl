---
title: Plik polecenia BSCMAKE (plik odpowiedzi) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1d5dd2696a48a84672350b90b569c8f0caf7c3cd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="bscmake-command-file-response-file"></a>Plik polecenia BSCMAKE (Plik odpowiedzi)
Możesz podać części lub całości danych wejściowych wiersza polecenia w pliku poleceń. Określ plik polecenia, używając następującej składni:  
  
```  
BSCMAKE @filename  
```  
  
 Dozwolone jest tylko jedno polecenie pliku. Można określić ścieżki z *filename*. Należy poprzedzić *filename* z znak @ (@). BSCMAKE nie zakłada się rozszerzeniem. Możesz określić dodatkowe *sbrfiles* w wierszu polecenia, po *filename*. Plik polecenia to plik tekstowy, który zawiera dane wejściowe BSCMAKE w tej samej kolejności, ponieważ należy ją określić w wierszu polecenia. Argumenty wiersza polecenia oddzielić co najmniej jeden spacje, tabulatory lub znakami nowego wiersza.  
  
 Polecenie wywołuje BSCMAKE przy użyciu pliku polecenia:  
  
```  
BSCMAKE @prog1.txt  
```  
  
 Poniżej przedstawiono przykładowy plik polecenia:  
  
```  
/n /v /o main.bsc /El  
/S (  
toolbox.h  
verdate.h c:\src\inc\screen.h  
)  
file1.sbr file2.sbr file3.sbr file4.sbr  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie BSCMAKE](../../build/reference/bscmake-reference.md)