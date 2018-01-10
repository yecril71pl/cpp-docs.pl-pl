---
title: -APPCONTAINER | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /APPCONTAINER
dev_langs: C++
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 19e926cbfd1fc58e04c8370825dd83eacff05dfe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="appcontainer"></a>/APPCONTAINER
Oznacza plik wykonywalny, który musi zostać uruchomiony w kontenerze aplikacji — na przykład [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] lub aplikacji uniwersalnej systemu Windows.  
  
```  
  
/APPCONTAINER[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Plik wykonywalny, który ma **/APPCONTAINER** zestaw opcji może być uruchamiany tylko w kontenerze aplikacji, czyli środowisku izolacji procesu, wprowadzone w systemie Windows 8. Aby uzyskać [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] i aplikacji uniwersalnych systemu Windows musi być ustawiona opcja.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje polecenia EDITBIN](../../build/reference/editbin-options.md)   
 [Co to jest aplikacji uniwersalnej systemu Windows?](http://go.microsoft.com/fwlink/p/?LinkID=522074)