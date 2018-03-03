---
title: "Błąd krytyczny NMAKE U1051 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- U1051
dev_langs:
- C++
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93c109bf723b3c4cf08e998a715fe8f6f33be466
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1051"></a>Błąd krytyczny NMAKE U1051
Za mało pamięci  
  
 NMAKE za mało pamięci, w tym pamięci wirtualnej, ponieważ plik makefile był za duży lub zbyt złożony.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Zwolnij miejsce na dysku.  
  
2.  Zwiększenie rozmiaru pliku stronicowania systemu Windows NT lub wymiany systemu Windows.  
  
3.  Jeśli tylko część pliku reguł programu make jest używany, podział pliku reguł programu make oddzielnych plików albo użyj **! Jeśli** dyrektywy, aby ograniczyć, który może przetwarzać NMAKE przetwarzania wstępnego. **! Jeśli** obejmują dyrektywy **! Jeśli**, `!IFDEF`, **! IFNDEF**, **! ELSE IF**, **! ELSE** `IFDEF`, i **! ELSE** `IFNDEF`.