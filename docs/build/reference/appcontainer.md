---
title: -APPCONTAINER | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /APPCONTAINER
dev_langs:
- C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c47154d7a5eddd26573612708462c0352da30ae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368437"
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