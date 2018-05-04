---
title: try-finally Statement (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54e33f4648861e872ab8d866930d3412a56a5ef4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="try-finally-statement-c"></a>try-finally — instrukcja (C)
**Microsoft Specific**  
  
 `try-finally` Instrukcja jest rozszerzeniem firmy Microsoft dla języka C, umożliwiającą aplikacjom zagwarantować wykonywanie czyszczenia kodu po przerwaniu wykonywania bloku kodu. Oczyszczanie składa się z zadania, takie jak cofanie przydziału pamięci, zamykanie plików i zwalniania dojść do plików. `try-finally` Instrukcja jest szczególnie przydatne dla procedur, które mają kilku miejscach, w którym dokonuje wystąpił błąd, który może powodować przedwczesny zwracać rutynowych.  
  
 *try-finally — instrukcji*:  
 **__try***złożonej instrukcji*   
  
 **__finally***złożonej instrukcji*   
  
 Instrukcja złożona po `__try` klauzula jest zabezpieczona sekcji. Instrukcja złożona po `__finally` klauzula jest programu obsługi zakończenia. Program obsługi określa zestaw akcji, które są wykonywane po sekcji ochroną zostanie zakończone, czy sekcji ochroną jest zakończony przez wyjątek (przerwania pracy) lub standardowy poniżej (normalne zakończenia).  
  
 Kontrolowanie osiągnie `__try` oświadczenie proste wykonywanie kolejnych (poniżej). Gdy formant przechodzi `__try` instrukcji, jego skojarzony program obsługi staje się aktywny. Wykonanie przebiega w następujący sposób:  
  
1.  Sekcja chroniona jest wykonywana.  
  
2.  Programu obsługi zakończenia jest wywoływany.  
  
3.  Po zakończeniu działania programu obsługi zakończenia wykonanie jest kontynuowane po `__finally` instrukcji. Niezależnie od tego, jak chroniony kończy się w sekcji (na przykład za pomocą `goto` instrukcji poza ochroną treści lub za pośrednictwem `return` instrukcji), programu obsługi zakończenia jest wykonywany przed przepływu sterowania zostanie przeniesiona poza sekcji ochroną.  
  
 `__leave` — Słowo kluczowe jest prawidłowy w ramach `try-finally` blok instrukcji. Efekt `__leave` jest, aby przejść do końca `try-finally` bloku. Programu obsługi zakończenia natychmiast została wykonana. Mimo że `goto` instrukcja może być używana do wykonania takiego samego wyniku `goto` instrukcja powoduje odwijanie stosu. `__leave` Instrukcja jest bardziej wydajne, ponieważ nie obejmuje odwijanie stosu.  
  
 Kończenie `try-finally` instrukcji przy użyciu `return` instrukcji lub `longjmp` funkcja czasu wykonywania jest uznawana za przerwania pracy. Jest niedozwolony skok do `__try` instrukcji, ale prawnych, aby przejść z jednego. Wszystkie `__finally` instrukcji, które są aktywne między punktem wyjścia i miejsce docelowe muszą być uruchamiane. Jest to "lokalne rozwinięcie".  
  
 Programu obsługi zakończenia nie jest wywoływana, gdy proces jest skasowane podczas wykonywania `try-finally` instrukcji.  
  
> [!NOTE]
>  Obsługa wyjątków strukturalnych współpracuje z pliki źródłowe C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Obsługa mechanizmu wyjątków C++ jest również bardziej elastyczne, w tym może obsłużyć wyjątki dowolnego typu.  
  
> [!NOTE]
>  W przypadku programów C++ C++, obsługa wyjątków należy użyć zamiast Obsługa wyjątków strukturalnych. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków](../cpp/exception-handling-in-visual-cpp.md) w *dokumentacja języka C++*.  
  
 Zobacz przykład [spróbuj-except — instrukcja](../c-language/try-except-statement-c.md) aby zobaczyć, jak `try-finally` works instrukcji.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [try-finally, instrukcja](../cpp/try-finally-statement.md)