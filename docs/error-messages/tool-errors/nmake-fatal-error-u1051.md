---
title: Błąd krytyczny NMAKE U1051 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1051
dev_langs:
- C++
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 570c7e5d8e6e8250a67e4f032ac26b04388cfd00
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="nmake-fatal-error-u1051"></a>Błąd krytyczny NMAKE U1051
Za mało pamięci  
  
 NMAKE za mało pamięci, w tym pamięci wirtualnej, ponieważ plik makefile był za duży lub zbyt złożony.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Zwolnij miejsce na dysku.  
  
2.  Zwiększenie rozmiaru pliku stronicowania systemu Windows NT lub wymiany systemu Windows.  
  
3.  Jeśli tylko część pliku reguł programu make jest używany, podział pliku reguł programu make oddzielnych plików albo użyj **! Jeśli** dyrektywy, aby ograniczyć, który może przetwarzać NMAKE przetwarzania wstępnego. **! Jeśli** obejmują dyrektywy **! Jeśli**, `!IFDEF`, **! IFNDEF**, **! ELSE IF**, **! ELSE** `IFDEF`, i **! ELSE** `IFNDEF`.