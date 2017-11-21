---
title: "Ostrzeżenie LNK4237 narzędzi konsolidatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4237
dev_langs: C++
helpviewer_keywords: LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8cc822d4e7432a0a603df9da78b7c4d244719a09
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4237"></a>Ostrzeżenie LNK4237 narzędzi konsolidatora
/SUBSYSTEM:NATIVE określony podczas importowania z 'dll'; Użyj opcji lub/Subsystem: Windows.  
  
 [/SUBSYSTEM:NATIVE](../../build/reference/subsystem-specify-subsystem.md) został określony podczas tworzenia aplikacji systemu windows (Win32), który bezpośrednio jest używana co najmniej jeden z następujących czynności:  
  
-   Kernel32.dll  
  
-   Gdi32.dll  
  
-   User32.dll  
  
-   jeden z biblioteki DLL msvcrt *.  
  
 Rozwiązanie to ostrzeżenie, nie określając **/SUBSYSTEM:NATIVE**.