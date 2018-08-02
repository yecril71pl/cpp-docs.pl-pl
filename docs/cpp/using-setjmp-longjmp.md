---
title: Użycie funkcji setjmp-longjmp | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 2073729fc5445fc36e3d8a6f52c4f69b079c8b47
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462134"
---
# <a name="using-setjmplongjmp"></a>Użycie funkcji setjmp/longjmp
Gdy [setjmp](../c-runtime-library/reference/setjmp.md) i [longjmp](../c-runtime-library/reference/longjmp.md) są używane razem, zapewniają sposób wykonania nielokalnych **goto**. One zazwyczaj są używane do przekazywania formantów wykonywania do kodu obsługi błędów lub odzyskiwania w poprzednio wywołanej procedurze bez użycia standardowego wywołania lub Konwencji zwracania.  
  
> [!CAUTION]
>  Jednak ponieważ **setjmp** i **longjmp** nie obsługują semantyki obiektów języka C++ i ponieważ one mogą zmniejszyć wydajność poprzez zapobieganie optymalizacji w zmiennych lokalnych, zalecamy, aby używać ich w programach języka C++. Firma Microsoft zaleca użycie **spróbuj**/**catch** tworzy zamiast tego.  
  
 Jeśli zdecydujesz się używać **setjmp**/**longjmp** w programie C++, również obejmować \<setjmp.h > lub \<setjmpex.h > Aby zapewnić poprawne interakcji między Funkcje i obsługa wyjątków języka C++. Jeśli używasz [/EH](../build/reference/eh-exception-handling-model.md) do kompilowania, destruktory obiektów lokalnych są wywoływane podczas odwijania stosu. Jeśli używasz **/EHS** do kompilacji, a jedna z funkcji wywołuje funkcję, która używa [nothrow](../cpp/nothrow-cpp.md) i funkcję, która używa **nothrow** wywołania **longjmp**, a następnie odwijanie przez destruktora może nie występować, w zależności od optymalizatora.  
  
 W kodzie przenośnym, gdy nielokalna **goto** wywołująca **longjmp** jest wykonywana, prawidłowe niszczenie obiektów opartych na klatkach może być zawodne.  
  
## <a name="see-also"></a>Zobacz także  
 [Połączenie wyjątków języka C (strukturalnych) i C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)