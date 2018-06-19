---
title: Błąd matematyczny M6108 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6108
dev_langs:
- C++
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4dfeca48aa04ebfbc097649e5c25253166c50dad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325854"
---
# <a name="math-error-m6108"></a>Błąd matematyczny M6108
pierwiastek kwadratowy  
  
 Argument operacji pierwiastek kwadratowy była ujemna.  
  
 Program kończy się z kodem zakończenia 136.  
  
> [!NOTE]
>  `sqrt` Funkcja biblioteki wykonawczej języka C i Wewnętrzna funkcja FORTRAN **SQRT** nie generują ten błąd. C `sqrt` funkcja sprawdza argument przed wykonaniem tej operacji i zwraca wartość błędu, jeśli argument jest ujemna. FORTRAN **SQRT** funkcja generuje błąd domeny [M6201](../../error-messages/tool-errors/math-error-m6201.md) zamiast tego błędu.