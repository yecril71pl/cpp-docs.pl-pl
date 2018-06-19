---
title: Błąd kompilatora zasobów RC2001 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2001
dev_langs:
- C++
helpviewer_keywords:
- RC2001
ms.assetid: 92bfb4c0-1879-4606-bb9f-ef7368707b4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ef1fd5d29fc5784ee418a8456cacec37e943b73
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322422"
---
# <a name="resource-compiler-error-rc2001"></a>Błąd kompilatora zasobów RC2001
nowy wiersz w stałej  
  
 Stała znakowa była kontynuowana w drugim wierszu bez ukośnik odwrotny (**\\**) lub zamknięcia i otwarcia podwójny cudzysłów (**"**).  
  
 Aby przerwać stałą typu string, który znajduje się na dwa wiersze w pliku źródłowym, wykonaj jedną z następujących czynności:  
  
-   Zakończenie pierwszy wiersz z znak kontynuacji wiersza, ukośnik odwrotny.  
  
-   Zamknij ten ciąg w pierwszym wierszu podwójny cudzysłów i otwórz ciągu w następnym wierszu innego znaku cudzysłowu.  
  
 Nie jest wystarczające, aby zakończyć pierwszy wiersz z \n, sekwencja specjalna osadzania znaku nowego wiersza w stałą typu string.