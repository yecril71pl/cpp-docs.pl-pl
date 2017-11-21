---
title: "Przykładowe pliku reguł programu make | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 8343ce71-5556-4ae0-8d1e-7efd82673070
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 845c1c5d816b1553ed63a3c2d520c5489ecffeea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="sample-makefile"></a>Przykładowy plik pliku reguł programu Make
Ten temat zawiera przykładowy pliku reguł programu make.  
  
## <a name="sample"></a>Przykład  
  
### <a name="code"></a>Kod  
  
```  
# Sample makefile  
  
!include <win32.mak>  
  
all: simple.exe challeng.exe  
  
.c.obj:  
  $(cc) $(cdebug) $(cflags) $(cvars) $*.c  
  
simple.exe: simple.obj  
  $(link) $(ldebug) $(conflags) -out:simple.exe simple.obj $(conlibs) lsapi32.lib  
  
challeng.exe: challeng.obj md4c.obj  
  $(link) $(ldebug) $(conflags) -out:challeng.exe $** $(conlibs) lsapi32.lib  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zawartość pliku reguł programu make](../build/contents-of-a-makefile.md)