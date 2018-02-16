---
title: -APPCONTAINER | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /APPCONTAINER
dev_langs:
- C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 08966cd2b9da434c45750edb57644c182a14baf2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="appcontainer"></a>/APPCONTAINER
Oznacza plik wykonywalny, który musi zostać uruchomiony w kontenerze aplikacji — na przykład aplikację Microsoft Store lub uniwersalnych systemu Windows.  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Plik wykonywalny, który ma **/APPCONTAINER** zestaw opcji może być uruchamiany tylko w kontenerze aplikacji, czyli środowisku izolacji procesu, wprowadzone w systemie Windows 8. W przypadku aplikacji Microsoft Store i uniwersalnych systemu Windows można ustawić tę opcję.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje polecenia EDITBIN](../../build/reference/editbin-options.md)   
 [Co to jest aplikacji uniwersalnej systemu Windows?](http://go.microsoft.com/fwlink/p/?LinkID=522074)