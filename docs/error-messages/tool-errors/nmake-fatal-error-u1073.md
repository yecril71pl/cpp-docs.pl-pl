---
title: "Błąd krytyczny NMAKE U1073 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1073
dev_langs: C++
helpviewer_keywords: U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cc68305e5866c9765cba6bcdc1e4ac3ba17fce64
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1073"></a>Błąd krytyczny NMAKE U1073
nie wiadomo, jak "targetname"  
  
 Określony element docelowy nie istnieje, a nie istnieje lub aby zastosować regułę wnioskowania polecenie do wykonania.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać problem przy użyciu następujących możliwych rozwiązań  
  
1.  Sprawdź pisownię nazwy docelowego.  
  
2.  Jeśli *targetname* jest pseudotarget, określ ją jako miejsce docelowe w innym bloku opis.  
  
3.  Jeśli *targetname* jest wywołanie makra, pamiętaj, że nie zwiększa się pusty ciąg.