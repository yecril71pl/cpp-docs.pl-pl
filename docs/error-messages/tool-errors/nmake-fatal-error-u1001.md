---
title: "Błąd krytyczny NMAKE U1001 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1001
dev_langs: C++
helpviewer_keywords: U1001
ms.assetid: 5d7da559-6cbd-44d6-848c-aaf54cae0d1a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 17cac891bdb75f786ea1c0bc6119afe2b80f290b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1001"></a>Błąd krytyczny NMAKE U1001
Błąd składni: niedozwolony znak "character" w makrze  
  
 Podany znak pojawia się w makrze, ale nie jest literą, cyfrą lub podkreślenia.  
  
 Przyczyną tego błędu może być brak dwukropka w rozwinięciu makra:  
  
```  
syntax error : illegal character '=' in macro  
```