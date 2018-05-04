---
title: -DYNAMICBASE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /dynamicbase
dev_langs:
- C++
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d7a4cf7aa35d7ad6b41fc6d61f3f27662ae2c8d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="dynamicbase"></a>/DYNAMICBASE
Określa, czy obraz wykonywalny może być losowo przebazowanych w czasie ładowania przy użyciu randomizacji układu przestrzeni adresowej (ASLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
/DYNAMICBASE[:NO]  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie ustawia konsolidator **/DYNAMICBASE** opcji.  
  
 Ta opcja modyfikuje nagłówek obrazu wykonywalnego, aby wskazać, czy moduł ładujący mogą losowo rebase obrazu w czasie ładowania.  
  
 ASLR jest obsługiwana w systemach Windows Vista, Windows Server 2008, Windows 7, Windows 8 i Windows Server 2012.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje polecenia EDITBIN](../../build/reference/editbin-options.md)   
 [Poziom ochrony oprogramowania niezależnego dostawcy oprogramowania systemu Windows](http://msdn.microsoft.com/library/bb430720.aspx)