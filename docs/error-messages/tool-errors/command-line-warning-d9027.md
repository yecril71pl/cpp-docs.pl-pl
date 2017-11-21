---
title: "D9027 dla wiersza ostrzeżenie polecenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: D9027
dev_langs: C++
helpviewer_keywords: D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5ccdccbc4c6df8f948b44eeaa096cff46824d043
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="command-line-warning-d9027"></a>Ostrzeżenie D9027 dla wiersza polecenia
plik źródłowy "\<nazwa pliku >" ignorowane  
  
 CL.exe ignorowane pliku źródła danych wejściowych.  
  
 To ostrzeżenie może być spowodowane odstęp między opcja /Fo i nazwę pliku wyjściowego w wierszu polecenia z opcją/c. Na przykład:  
  
```  
cl /c /Fo output.obj input.c   
```  
  
 Ponieważ istnieje odstęp między /Fo i `output.obj`, przyjmuje CL.exe `output.obj` jako nazwa pliku wejściowego. Aby rozwiązać ten problem, Usuń miejsce:  
  
```  
cl /c /Fooutput.obj input.c   
```