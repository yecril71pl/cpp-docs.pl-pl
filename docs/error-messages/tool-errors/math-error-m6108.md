---
title: "Błąd matematyczny M6108 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- M6108
dev_langs:
- C++
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6db123d9cb96274848a3edd9f845f86f413d8e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6108"></a>Błąd matematyczny M6108
pierwiastek kwadratowy  
  
 Argument operacji pierwiastek kwadratowy była ujemna.  
  
 Program kończy się z kodem zakończenia 136.  
  
> [!NOTE]
>  `sqrt` Funkcja biblioteki wykonawczej języka C i Wewnętrzna funkcja FORTRAN **SQRT** nie generują ten błąd. C `sqrt` funkcja sprawdza argument przed wykonaniem tej operacji i zwraca wartość błędu, jeśli argument jest ujemna. FORTRAN **SQRT** funkcja generuje błąd domeny [M6201](../../error-messages/tool-errors/math-error-m6201.md) zamiast tego błędu.