---
title: try-finally — instrukcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- __try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
dev_langs:
- C++
helpviewer_keywords:
- __try keyword [C++]
- __finally keyword [C++]
- __leave keyword [C++]
- try-catch keyword [C++], try-finally keyword
- try-finally keyword [C++]
- __finally keyword [C++], try-finally statement syntax
- __leave keyword [C++], try-finally statement
- structured exception handling [C++], try-finally
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c57676cace8451de266d30d4c146e3ae0c3cb1b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="try-finally-statement"></a>try-finally — instrukcja
**Dotyczące firmy Microsoft**  
  
 W tym artykule opisano następującej składni `try-finally` instrukcji:  
  
```  
__try {  
   // guarded code  
}  
__finally {  
   // termination code  
}  
```  
  
## <a name="grammar"></a>Gramatyka  
 *try-finally — instrukcji*:  
 `__try`*złożonej instrukcji*  
  
 `__finally`*złożonej instrukcji*  
  
 `try-finally` Instrukcja jest rozszerzenia Microsoft do języków C i C++, umożliwiającą aplikacjom docelowy gwarantuje wykonywanie czyszczenia kodu, gdy wykonanie bloku kodu zostanie przerwane. Oczyszczanie składa się z zadania, takie jak cofanie przydziału pamięci, zamykanie plików i zwalniania dojść do plików. `try-finally` Instrukcja jest szczególnie przydatne dla procedur, które mają kilku miejscach, w którym dokonuje wystąpił błąd, który może powodować przedwczesny zwracać rutynowych.  
  
 Informacje pokrewne i przykładowy kod, zobacz [spróbuj-except — instrukcja](../cpp/try-except-statement.md). Aby uzyskać więcej informacji na ogólnie obsługi wyjątków strukturalnych, zobacz [obsługi wyjątków strukturalnych](../cpp/structured-exception-handling-c-cpp.md). Aby uzyskać więcej informacji dotyczących obsługi wyjątków w aplikacji zarządzanych, zobacz [obsługi wyjątków w/CLR](../windows/exception-handling-cpp-component-extensions.md).  
  
> [!NOTE]
>  Strukturalna obsługa wyjątków działa z Win32 dla plików źródłowych C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto, obsługa wyjątków C++ jest bardziej elastyczna, gdyż może obsługiwać wyjątki dowolnego typu. Dla programów C++, zaleca się użycie mechanizmu obsługi wyjątków języka C++ ([spróbuj, catch i zgłosić](../cpp/try-throw-and-catch-statements-cpp.md) instrukcje).  
  
 Instrukcja złożona po `__try` klauzula jest zabezpieczona sekcji. Instrukcja złożona po `__finally` klauzula jest programu obsługi zakończenia. Program obsługi określa zestaw akcji, które są wykonywane, gdy ochroną sekcji zostanie zakończone, niezależnie od tego, czy został zakończony sekcji ochroną przez wyjątek (przerwania pracy) lub standardowy poniżej (normalne zakończenia).  
  
 Kontrolowanie osiągnie `__try` oświadczenie proste wykonywanie kolejnych (poniżej). Gdy formant przechodzi `__try`, aktywne staje się jego skojarzony program obsługi. Jeśli przepływu sterowania dociera do końca bloku try, wykonanie przebiega w następujący sposób:  
  
1.  Programu obsługi zakończenia jest wywoływany.  
  
2.  Po zakończeniu działania programu obsługi zakończenia wykonanie jest kontynuowane po `__finally` instrukcji. Niezależnie od tego, jak chroniony kończy się w sekcji (na przykład za pomocą `goto` poza ochroną treści lub `return` instrukcji), programu obsługi zakończenia jest wykonywany `before` przepływu sterowania zostanie przeniesiona poza sekcji ochroną.  
  
     A **__finally** instrukcji nie blokuje wyszukiwanie obsługi odpowiednich wyjątków.  
  
 Jeśli wystąpi wyjątek w `__try` bloku, system operacyjny musi odnaleźć program obsługi wyjątku lub program zakończy się niepowodzeniem. Jeśli program obsługi zostanie znaleziony, wszystkie `__finally` bloki są wykonywane i wznawia wykonywanie programu obsługi.  
  
 Załóżmy na przykład, szereg wywołania funkcji łącza funkcji A działanie D, jak pokazano na poniższej ilustracji. Każda funkcja ma jeden programu obsługi zakończenia. Jeśli wyjątek jest zgłaszany w funkcji D i obsługiwane A, programy obsługi zakończenia są nazywane w tej kolejności, jak system cofa stosu: D-C, B.  
  
 ![Kolejność zakończenia &#45; wykonywanie programu obsługi](../cpp/media/vc38cx1.gif "vc38CX1")  
Kolejność wykonywania programu obsługi zakończenia  
  
> [!NOTE]
>  Zachowanie try-finally różni się od innych języków, które obsługują **koniec**, takich jak C#.  Pojedynczy `__try` może mieć albo, ale nie obu z `__finally` i `__except`.  Jeśli oba mają być używane razem, spróbuj zewnętrzne — z wyjątkiem instrukcji należy ująć w instrukcji wewnętrzny try-finally.  Reguły podczas każdego bloku wykonuje również są różne.  
  
## <a name="the-leave-keyword"></a>Słowo kluczowe __leave  
 Słowo kluczowe `__leave` jest prawidłowe tylko wewnątrz sekcji chronionej wyrażenia `try-finally` a jego efektem jest przeskoczenie do końca sekcji chronionej. Wykonywanie będzie kontynuowane przy pierwszej instrukcji w programu obsługi zakończenia.  
  
 A `goto` instrukcja również może wykonać skok poza sekcji ochroną, ale obniża wydajność, ponieważ wywołuje ona odwijanie stosu. `__leave` Instrukcja jest bardziej wydajne, ponieważ nie powoduje odwijanie stosu.  
  
## <a name="abnormal-termination"></a>Przerwania pracy  
 Kończenie `try-finally` instrukcji przy użyciu [longjmp](../c-runtime-library/reference/longjmp.md) funkcja czasu wykonywania jest uznawana za przerwania pracy. Jest niedozwolony skok do `__try` instrukcji, ale prawnych, aby przejść z jednego. Wszystkie `__finally` instrukcji, które są aktywne między punktem wyjścia (normalne zakończenia `__try` bloku) i miejscu docelowym ( `__except` bloku, który obsługuje wyjątek) musi być uruchamiane. Jest to lokalne odwinięcie.  
  
 Jeśli **spróbuj** przedwcześnie z jakiegokolwiek powodu, w tym skok poza blokiem bloku, system wykonuje skojarzony **koniec** blok odwijanie stosu w ramach procesu. W takich przypadkach [AbnormalTermination](http://msdn.microsoft.com/library/windows/desktop/ms679265) funkcja zwraca wartość PRAWDA, jeśli wywoływana z poziomu **koniec** zablokować; w przeciwnym razie zwraca wartość FALSE.  
  
 Programu obsługi zakończenia nie jest wywoływana, gdy proces skasowane jest w trakcie wykonywania `try-finally` instrukcji.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)   
 [(C/C++) obsługi wyjątków strukturalnych](../cpp/structured-exception-handling-c-cpp.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)   
 [Składnia programu obsługi zakończenia](http://msdn.microsoft.com/library/windows/desktop/ms681393)