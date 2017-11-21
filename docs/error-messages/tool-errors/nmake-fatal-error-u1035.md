---
title: "Błąd krytyczny NMAKE U1035 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1035
dev_langs: C++
helpviewer_keywords: U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a4d672618656b72ab7ac4c4ed617c90080b58304
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="nmake-fatal-error-u1035"></a>Błąd krytyczny NMAKE U1035
Błąd składniowy: oczekiwano ":" lub "=" separatora  
  
 Albo dwukropkiem (**:**) lub znak równości (**=**) był oczekiwany.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Dwukropek nie wykonaj obiektu docelowego.  
  
2.  Dwukropek i bez spacji (na przykład a:), a następnie docelowy pojedynczej litery. NMAKE zinterpretować go jako specyfikację dysku.  
  
3.  Dwukropek nie wykonaj reguła wnioskowania.  
  
4.  Znak równości nie nastąpiła definicji makra.  
  
5.  Znak, a następnie ukośnik odwrotny (**\\**) użytą do kontynuowania polecenia do nowego wiersza.  
  
6.  Pojawił się ciąg, który nie istniała NMAKE reguły składni.  
  
7.  Plik makefile sformatowano go przy użyciu edytora tekstu.