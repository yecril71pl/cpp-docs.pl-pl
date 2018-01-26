---
title: "Użycie funkcji setjmp longjmp | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- longjmp_cpp
- setjmp_cpp
dev_langs: C++
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fede2e7865ab002d77a174a28928df491b29981
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2018
---
# <a name="using-setjmplongjmp"></a>Użycie funkcji setjmp/longjmp
Gdy [setjmp](../c-runtime-library/reference/setjmp.md) i [longjmp](../c-runtime-library/reference/longjmp.md) są używane razem, umożliwiają wykonanie innego niż lokalne `goto`. One są zwykle używane do przekazania Kontrola wykonywania kodu służącego do obsługi błędów lub odzyskiwania w wcześniej wywołana procedura bez przy użyciu standardowych telefonicznej lub return Konwencji.  
  
> [!CAUTION]
>  Jednak ponieważ `setjmp` i `longjmp` nie obsługują semantyki obiektu języka C++, a ponieważ one może zmniejszyć wydajność, zapobiegając optymalizacji na zmiennych lokalnych, zalecamy nie stosowanie ich w programach języka C++. Firma Microsoft zaleca użycie `try` / `catch` tworzy zamiast tego.  
  
 Jeśli zdecydujesz się używać `setjmp` / `longjmp` w programu C++ również obejmować \<setjmp.h > lub \<setjmpex.h > Aby zapewnić poprawne interakcji pomiędzy funkcjami i C++, obsługa wyjątków. Jeśli używasz [/EH](../build/reference/eh-exception-handling-model.md) skompilować, zostaną wywołane destruktory dla obiektów lokalnych podczas unwind stosu. Jeśli używasz **/EHS** do kompilacji, a drugi z wywołań funkcji, a funkcja, która używa [nothrow](../cpp/nothrow-cpp.md) i funkcję, która używa `nothrow` wywołania `longjmp`, następnie unwind destruktor nie może wystąpić, w zależności od optymalizacji.  
  
 W kodzie przenośny, gdy nie lokalnego `goto` , który odwołuje się `longjmp` jest wykonywane, poprawne niszczenie obiektów na podstawie ramki mogą być zawodne.  
  
## <a name="see-also"></a>Zobacz też  
 [Połączenie wyjątków języka C (strukturalnych) i C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)