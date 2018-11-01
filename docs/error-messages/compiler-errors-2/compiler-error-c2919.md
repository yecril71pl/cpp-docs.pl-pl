---
title: Błąd kompilatora C2919
ms.date: 11/04/2016
f1_keywords:
- C2919
helpviewer_keywords:
- C2919
ms.assetid: 140a6db9-eb48-4c5e-84a7-a09d2653605b
ms.openlocfilehash: ab11226c8cc4629a265dd182d5f882f6b3be7e5d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577661"
---
# <a name="compiler-error-c2919"></a>Błąd kompilatora C2919

"type": nie można używać operatorów na publikowanej powierzchni typu WinRT

System typów środowiska wykonawczego Windows nie obsługuje operatora elementów członkowskich w publikowanej powierzchni typu. Jest to, ponieważ nie wszystkie języki mogą wykorzystywać operator elementów członkowskich. Operator prywatny lub wewnętrzny można utworzyć funkcji elementów członkowskich, które mogą być wywoływane z poziomu kodu C++ w tej samej jednostce klasy lub kompilacji.

Aby rozwiązać ten problem, Usuń operatora funkcji składowej z publicznego interfejsu, lub zmień go na funkcję nazwanego elementu członkowskiego. Na przykład, zamiast z `operator==`, nadaj nazwę funkcji składowej `Equals`.