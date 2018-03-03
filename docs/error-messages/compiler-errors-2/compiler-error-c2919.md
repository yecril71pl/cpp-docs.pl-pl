---
title: "C2919 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2919
dev_langs:
- C++
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4e2bde12c4c6ffa94f55e9dd205c3132a755ad94
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2919"></a>C2919 błąd kompilatora
'type': nie można używać operatorów na publikowanej powierzchni typu WinRT  
  
 System typów środowiska wykonawczego systemu Windows nie obsługuje funkcji Członkowskich operatora w publikowanej powierzchni typu. Jest to, ponieważ nie wszystkie języki, jaką może wykorzystać funkcje Członkowskie operatora. Operator prywatny lub wewnętrzny można utworzyć funkcji elementów członkowskich, które mogą być wywoływane z kodu C++ w tej samej jednostce kompilacji lub klasy.  
  
 Aby rozwiązać ten problem, Usuń operator funkcji członkowskiej z interfejs publiczny, lub zmień ją na funkcji o nazwie elementu członkowskiego. Na przykład zamiast z `operator==`, nazwy funkcji członkowskiej `Equals`.