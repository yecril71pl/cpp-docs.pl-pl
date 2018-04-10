---
title: Uruchomienie NMAKE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- targets, building
- response files, NMAKE
- targets
- command files
- NMAKE program, targets
- NMAKE program, running
- command files, NMAKE
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6c39612cf4df47665f7ea3d529b77ee4e70ce8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="running-nmake"></a>Uruchomienie NMAKE
## <a name="syntax"></a>Składnia  
  
```  
NMAKE [option...] [macros...] [targets...] [@commandfile...]  
```  
  
## <a name="remarks"></a>Uwagi  
 Określony tylko kompilacje NMAKE *cele* lub, jeśli nie zostanie określona, pierwszy obiektów docelowych w pliku reguł programu make. Pierwszy element docelowy pliku reguł programu make może być [pseudotarget](../build/pseudotargets.md) które kompilacje innych celów. Pliki reguł programu make określony za pomocą /F; używa NMAKE Jeśli nie określono /F, używa plik pliku reguł programu make w bieżącym katalogu. Jeśli określono pliku makefile, zasady wnioskowania używa do kompilacji wiersza polecenia *cele*.  
  
 `commandfile` Pliku tekstowego (lub plik odpowiedzi) zawiera danych wejściowych wiersza polecenia. Inne dane wejściowe mogą przed lub po`commandfile`. Ścieżka jest dozwolone. W `commandfile`, podziały wiersza są traktowane jako spacje. Należy ująć w cudzysłów definicje makr, jeśli zawierać spacji.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
 [Opcje NMAKE](../build/nmake-options.md)  
  
 [Tools.ini i NMAKE](../build/tools-ini-and-nmake.md)  
  
 [Kody zakończenia z NMAKE](../build/exit-codes-from-nmake.md)  
  
## <a name="see-also"></a>Zobacz też  
 [NMAKE — dokumentacja](../build/nmake-reference.md)