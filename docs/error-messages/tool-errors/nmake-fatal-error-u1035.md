---
title: Błąd krytyczny NMAKE U1035 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1035
dev_langs:
- C++
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bb32f815345b933ad6a65a0c8c1ec8ad59cbe81
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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