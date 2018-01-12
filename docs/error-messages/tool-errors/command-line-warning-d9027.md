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
ms.workload: cplusplus
ms.openlocfilehash: 2769eb5f78cb1d5bdd6749e65429d83b69a2807b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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