---
title: "Błąd narzędzi konsolidatora LNK1106 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1106
dev_langs: C++
helpviewer_keywords: LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 793d788462a3a449c654c30ec874399a3bb85728
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1106"></a>Błąd narzędzi konsolidatora LNK1106
Nieprawidłowy plik lub dysk jest pełny: nie można przejść do lokalizacji  
  
 Narzędzia nie można odczytać lub zapisać `location` w pliku mapowanych na pamięć.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Dysk jest zapełniony.  
  
     Zwolnij miejsce, a następnie połącz się ponownie.  
  
2.  Podjęto próbę połączenia za pośrednictwem sieci.  
  
     Niektóre sieci nie obsługują w pełni plików mapowanych na pamięć używanych przez konsolidator. Spróbuj łączenie na lokalnym dysku twardym.  
  
3.  Nieprawidłowy blok na dysku.  
  
     Mimo że dysku sprzętu i systemu operacyjnego należy wykryły takiego błędu, możesz uruchomić program sprawdzania dysku.  
  
4.  Za mało miejsca na stercie.  
  
     Zobacz [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) Aby uzyskać więcej informacji.