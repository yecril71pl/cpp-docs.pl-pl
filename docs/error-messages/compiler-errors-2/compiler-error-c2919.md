---
title: Błąd kompilatora C2919 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5d6ee01e32cd1855855fa6ac071af159be8bac0d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106834"
---
# <a name="compiler-error-c2919"></a>Błąd kompilatora C2919

"type": nie można używać operatorów na publikowanej powierzchni typu WinRT

System typów środowiska wykonawczego Windows nie obsługuje operatora elementów członkowskich w publikowanej powierzchni typu. Jest to, ponieważ nie wszystkie języki mogą wykorzystywać operator elementów członkowskich. Operator prywatny lub wewnętrzny można utworzyć funkcji elementów członkowskich, które mogą być wywoływane z poziomu kodu C++ w tej samej jednostce klasy lub kompilacji.

Aby rozwiązać ten problem, Usuń operatora funkcji składowej z publicznego interfejsu, lub zmień go na funkcję nazwanego elementu członkowskiego. Na przykład, zamiast z `operator==`, nadaj nazwę funkcji składowej `Equals`.