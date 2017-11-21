---
title: "Błąd kompilatora zasobów RC2001 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC2001
dev_langs: C++
helpviewer_keywords: RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 23b853db3cbea89bf9cb1ba43607c312e5264394
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="resource-compiler-error-rc2001"></a>Błąd kompilatora zasobów RC2001
nowy wiersz w stałej  
  
 Stała znakowa była kontynuowana w drugim wierszu bez ukośnik odwrotny (**\\**) lub zamknięcia i otwarcia podwójny cudzysłów (**"**).  
  
 Aby przerwać stałą typu string, który znajduje się na dwa wiersze w pliku źródłowym, wykonaj jedną z następujących czynności:  
  
-   Zakończenie pierwszy wiersz z znak kontynuacji wiersza, ukośnik odwrotny.  
  
-   Zamknij ten ciąg w pierwszym wierszu podwójny cudzysłów i otwórz ciągu w następnym wierszu innego znaku cudzysłowu.  
  
 Nie jest wystarczające, aby zakończyć pierwszy wiersz z \n, sekwencja specjalna osadzania znaku nowego wiersza w stałą typu string.