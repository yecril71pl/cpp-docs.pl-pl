---
title: Przy użyciu funkcji setjmp i longjmp | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- longjmp_cpp
- setjmp_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a83253fb98506bb586af2b52ef3321bada7ca01f
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2018
ms.locfileid: "42464661"
---
# <a name="using-setjmp-and-longjmp"></a>Przy użyciu funkcji setjmp i longjmp

Gdy [setjmp](../c-runtime-library/reference/setjmp.md) i [longjmp](../c-runtime-library/reference/longjmp.md) są używane razem, zapewniają sposób wykonania nielokalnych **goto**. One są zazwyczaj używane w kodzie języka C do przekazywania formantów wykonywania do kodu obsługi błędów lub odzyskiwania w poprzednio wywołanej procedurze bez użycia standardowego wywołania lub Konwencji zwracania.

> [!CAUTION]
> Ponieważ `setjmp` i `longjmp` nie obsługują prawidłowe niszczenie obiektów ramki stosu portably między kompilatorami C++ i ponieważ one mogą zmniejszyć wydajność poprzez zapobieganie optymalizacji w zmiennych lokalnych, nie zalecamy ich użycie w języku C++ programy. Zalecane jest użycie **spróbuj** i **catch** tworzy zamiast tego.

Jeśli zdecydujesz się używać `setjmp` i `longjmp` w programie C++, również obejmować \<setjmp.h > lub \<setjmpex.h > Aby zapewnić poprawne interakcji między funkcjami i wyjątków strukturalnych obsługi wyjątków (SEH) lub C++ Obsługa.

**Microsoft Specific**

Jeśli używasz [/EH](../build/reference/eh-exception-handling-model.md) opcji do kompilowania kodu C++, destruktory obiektów lokalnych są wywoływane podczas odwijania stosu. Jednak jeśli używasz **/EHS** lub **/ehsc** kompilacji i jednej funkcji, która używa [noexcept](../cpp/noexcept-cpp.md) wywołania `longjmp`, wówczas destruktor operacji unwind dla tej funkcji może nie występować, w zależności od stanu optymalizatora.

W kodzie przenośnym gdy `longjmp` wywołanie jest wykonywana, prawidłowe niszczenie obiektów opartych na klatkach jawnie nie jest gwarantowane przez standard i może nie być obsługiwana przez inne kompilatory. Cię powiadomić o poziom ostrzeżeń 4, wywołanie `setjmp` powoduje, że ostrzeżenie C4611: interakcja między "_setjmp powoduje" i zniszczeniem obiektu języka C++ nie jest przenośna.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Połączenie wyjątków języka C (strukturalnych) i C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)  
