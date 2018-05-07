---
title: C2919 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2919
dev_langs:
- C++
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5e2eb2a32f1a906814f5b347ba1ebf13eba71ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2919"></a>C2919 błąd kompilatora
'type': nie można używać operatorów na publikowanej powierzchni typu WinRT  
  
 System typów środowiska wykonawczego systemu Windows nie obsługuje funkcji Członkowskich operatora w publikowanej powierzchni typu. Jest to, ponieważ nie wszystkie języki, jaką może wykorzystać funkcje Członkowskie operatora. Operator prywatny lub wewnętrzny można utworzyć funkcji elementów członkowskich, które mogą być wywoływane z kodu C++ w tej samej jednostce kompilacji lub klasy.  
  
 Aby rozwiązać ten problem, Usuń operator funkcji członkowskiej z interfejs publiczny, lub zmień ją na funkcji o nazwie elementu członkowskiego. Na przykład zamiast z `operator==`, nazwy funkcji członkowskiej `Equals`.