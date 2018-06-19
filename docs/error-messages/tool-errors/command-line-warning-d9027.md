---
title: D9027 dla wiersza ostrzeżenie polecenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfe2493290c4e4cc5b744136b8e7036c6559220a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301453"
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