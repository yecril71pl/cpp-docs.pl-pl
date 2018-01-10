---
title: "Kompilatora (poziom 1) ostrzeżenie C4325 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4325
dev_langs: C++
helpviewer_keywords: C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ab31150efc02601d7392470198e162e979ac4917
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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