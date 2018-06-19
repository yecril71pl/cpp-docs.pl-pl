---
title: Kompilatora (poziom 1) ostrzeżenie C4788 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4788
dev_langs:
- C++
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19a43fb9d79c63637b2bff9a27661a9f848ef6dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284202"
---
# <a name="compiler-warning-level-1-c4788"></a>Kompilator C4788 ostrzegawcze (poziom 1)
'Identyfikator': identyfikator został obcięty do "number" znaków  
  
 Kompilator ogranicza maksymalną długość dozwoloną dla nazwy funkcji. Gdy kompilator generuje funclets dla kodu EH/SEH, wchodzi w skład nazwy funclet przez poprzedzenie jej nazwę funkcji z tekstem, na przykład "__catch", "\__unwind", lub innego ciągu.  
  
 Wynikowa nazwa funclet może być zbyt długi, a kompilator będzie ona truncate i generowanie C4788.  
  
 Aby usunąć to ostrzeżenie, Skróć oryginalną nazwę funkcji. Jeśli funkcja C++ szablonu funkcji lub metody, użyj jako element typedef dla części nazwy. Na przykład:  
  
```  
C1<x, y, z<T>>::C2<a,b,c>::f  
```  
  
 może być zastąpiony:  
  
```  
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;  
new_class::f  
```  
  
 To ostrzeżenie występuje tylko w [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] kompilatora.