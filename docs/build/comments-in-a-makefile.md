---
title: "Komentarze w pliku reguł programu make | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: makefiles, comments
ms.assetid: 76fd9e3d-5966-47f4-a091-c9e80b232b49
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7edfd0759c91adc75b77b0b320e2469722f5efc7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comments-in-a-makefile"></a>Komentarze w pliku reguł programu Make
Należy poprzedzić komentarza ze znakiem numeru (#). NMAKE pomija z znak liczby na następny znak nowego wiersza. Przykłady:  
  
```  
# Comment on line by itself  
OPTIONS = /MAP  # Comment on macro definition line  
  
all.exe : one.obj two.obj  # Comment on dependency line  
    link one.obj two.obj  
# Comment in commands block  
#   copy *.obj \objects  # Command turned into comment  
    copy one.exe \release  
  
.obj.exe:  # Comment on inference rule line  
    link $<  
  
my.exe : my.obj ; link my.obj  # Err: cannot comment this  
 # Error: # must be the first character  
.obj.exe: ; link $<  # Error: cannot comment this  
```  
  
 Aby określić znak numeru literału, należy poprzedzić daszek (**^**) w następujący sposób:  
  
```  
DEF = ^#define  #Macro for a C preprocessing directive  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zawartość pliku reguł programu make](../build/contents-of-a-makefile.md)