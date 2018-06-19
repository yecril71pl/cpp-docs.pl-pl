---
title: Błąd narzędzi konsolidatora LNK1106 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1106
dev_langs:
- C++
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3dedaa2bd500b11f06f9cfa98802fdd6ca84534
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298094"
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