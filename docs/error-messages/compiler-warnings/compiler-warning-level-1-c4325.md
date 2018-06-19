---
title: Kompilatora (poziom 1) ostrzeżenie C4325 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 936433987f823ae7d5d22cfd075f188dd5d4b1e4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277647"
---
# <a name="compiler-warning-level-1-c4325"></a>Kompilator C4325 ostrzegawcze (poziom 1)
**atrybuty dla standardowej sekcji "**   
 ***sekcja* "ignorowane**  
  
 Nie możesz zmienić atrybuty standardowej sekcji. Na przykład:  
  
```  
#pragma section(".sdata", long)  
```  
  
 Spowoduje to zastąpienie `.sdata` standardowa sekcja, która używa **krótki** typ danych **długi** — typ danych.  
  
 Zawiera sekcje standardowe atrybuty, których nie można zmieniać,  
  
-   .Data  
  
-   .sdata  
  
-   .BSS  
  
-   .sbss  
  
-   .Text  
  
-   .const —  
  
-   .sconst  
  
-   .rdata  
  
-   .srdata  
  
 Później można dodać dodatkowe sekcje.  
  
## <a name="see-also"></a>Zobacz też  
 [sekcja](../../preprocessor/section.md)