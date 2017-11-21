---
title: "Błąd matematyczny M6108 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: M6108
dev_langs: C++
helpviewer_keywords: M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6527a595673fddd9fe320097d093858d1c2c0ca1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="math-error-m6108"></a>Błąd matematyczny M6108
pierwiastek kwadratowy  
  
 Argument operacji pierwiastek kwadratowy była ujemna.  
  
 Program kończy się z kodem zakończenia 136.  
  
> [!NOTE]
>  `sqrt` Funkcja biblioteki wykonawczej języka C i Wewnętrzna funkcja FORTRAN **SQRT** nie generują ten błąd. C `sqrt` funkcja sprawdza argument przed wykonaniem tej operacji i zwraca wartość błędu, jeśli argument jest ujemna. FORTRAN **SQRT** funkcja generuje błąd domeny [M6201](../../error-messages/tool-errors/math-error-m6201.md) zamiast tego błędu.