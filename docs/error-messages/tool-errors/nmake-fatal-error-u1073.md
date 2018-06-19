---
title: Błąd krytyczny NMAKE U1073 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1073
dev_langs:
- C++
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dde9ca2f4a15edf6599dcc31b39d9411645f2a6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33316309"
---
# <a name="nmake-fatal-error-u1073"></a>Błąd krytyczny NMAKE U1073
nie wiadomo, jak "targetname"  
  
 Określony element docelowy nie istnieje, a nie istnieje lub aby zastosować regułę wnioskowania polecenie do wykonania.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Sprawdź pisownię nazwy docelowego.  
  
2.  Jeśli *targetname* jest pseudotarget, określ ją jako miejsce docelowe w innym bloku opis.  
  
3.  Jeśli *targetname* jest wywołanie makra, pamiętaj, że nie zwiększa się pusty ciąg.