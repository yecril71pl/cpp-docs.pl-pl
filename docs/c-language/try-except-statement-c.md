---
title: "Spróbuj — z wyjątkiem Statement (C) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9896e8a348a70ff6e27342f53f627097ef15dfa8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="try-except-statement-c"></a>try-except — instrukcja (C)
**Dotyczące firmy Microsoft**  
  
 **Spróbuj — z wyjątkiem** instrukcji to rozszerzenie firmy Microsoft dla języka C, który umożliwia aplikacjom przejąć kontrolę nad programu w przypadku wystąpienia zdarzenia, które zwykle na zakończenie wykonywania. Takie zdarzenia nazywane są wyjątkami, a mechanizm, który zajmuje się wyjątkami nazywa się strukturalną obsługą wyjątków.  
  
 Wyjątki mogą być albo lub oprogramowania sprzętowy. Nawet wtedy, gdy aplikacje nie mogą całkowicie odzyskać sprawności po wystąpieniu wyjątku sprzętowego lub programowego, strukturalna obsługa wyjątków umożliwia wyświetlenie informacji o błędzie i pozwala na przechwycenie wewnętrznego stanu aplikacji, aby pomóc w zdiagnozowaniu problemu. Jest to szczególnie użyteczne w przypadku sporadycznych problemów, których nie można łatwo odtworzyć.  
  
## <a name="syntax"></a>Składnia  
 *instrukcji z wyjątkiem try*:  
 **__try***złożonej instrukcji*   
  
 **__except (***wyrażenie***)***złożonej instrukcji*   
  
 Instrukcja złożona po `__try` klauzula jest zabezpieczona sekcji. Złożone wyrażenie po klauzuli `__except` to program obsługi wyjątków. Program obsługi określa zestaw akcji do wykonania, jeśli wyjątek zgłoszony podczas wykonywania sekcji ochroną. Wykonanie przebiega w następujący sposób:  
  
1.  Sekcja chroniona jest wykonywana.  
  
2.  Jeśli podczas wykonywania sekcji chronionej nie wystąpi wyjątek, program kontynuuje wykonywanie instrukcji po klauzuli `__except`.  
  
3.  Jeśli wystąpi wyjątek podczas wykonywania sekcji ochroną lub w dowolnej procedury wywołuje sekcji ochroną, `__except` wyrażenie jest obliczane i wartość zwracana określa sposób obsługi wyjątków. Istnieją trzy wartości:  
  
     `EXCEPTION_CONTINUE_SEARCH`Wyjątek nie został rozpoznany. Kontynuować wyszukiwanie górę stosu w przypadku obsługi najpierw zawierający **spróbuj — z wyjątkiem** instrukcje, a następnie dla programów obsługi o najwyższym priorytecie dalej.  
  
     `EXCEPTION_CONTINUE_EXECUTION`Wyjątek jest rozpoznany, ale zostanie odrzucony. Kontynuuj wykonywanie w punkcie, w którym wystąpił wyjątek.  
  
     `EXCEPTION_EXECUTE_HANDLER`Wyjątek został rozpoznany. Transfer kontroli do obsługi wyjątków, wykonując `__except` instrukcja złożona, a następnie kontynuować działanie w momencie Wystąpił wyjątek.  
  
 Ponieważ `__except` wyrażenie jest obliczane jako wyrażenie C, jest ograniczona do jednej wartości, operator wyrażenia warunkowego lub przecinka. Jeśli wymagane jest bardziej rozległe przetwarzanie, wyrażenie może wywołać procedurę, która zwraca jedną z trzech wartości wymienionych powyżej.  
  
> [!NOTE]
>  Obsługa wyjątków strukturalnych współpracuje z pliki źródłowe C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Obsługa mechanizmu wyjątków C++ jest również bardziej elastyczne, w tym może obsłużyć wyjątki dowolnego typu.  
  
> [!NOTE]
>  W przypadku programów C++ C++, obsługa wyjątków należy użyć zamiast Obsługa wyjątków strukturalnych. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków](../cpp/exception-handling-in-visual-cpp.md) w *dokumentacja języka C++*.  
  
 Każdej procedury w aplikacji może mieć własną obsługi wyjątków. `__except` Wyrażenie wykonuje się w zakresie `__try` treści. Oznacza to, że ma dostęp do wszelkich zmiennych lokalnych zadeklarowana.  
  
 `__leave` — Słowo kluczowe jest prawidłowy w ramach **spróbuj — z wyjątkiem** blok instrukcji. Efekt `__leave` jest, aby przejść do końca **spróbuj — z wyjątkiem** bloku. Wznawia wykonywanie po zakończeniu obsługi wyjątków. Mimo że `goto` instrukcja może być używana do wykonania takiego samego wyniku `goto` instrukcja powoduje odwijanie stosu. `__leave` Instrukcja jest bardziej wydajne, ponieważ nie obejmuje odwijanie stosu.  
  
 Kończenie **spróbuj — z wyjątkiem** instrukcji przy użyciu `longjmp` funkcja czasu wykonywania jest uznawana za przerwania pracy. Jest niedozwolony skok do `__try` instrukcji, ale prawnych, aby przejść z jednego. Program obsługi wyjątku nie jest wywoływana, gdy proces skasowane jest w trakcie wykonywania **spróbuj — z wyjątkiem** instrukcji.  
  
## <a name="example"></a>Przykład  
 Poniżej przedstawiono przykład program obsługi wyjątku i programu obsługi zakończenia. Zobacz [instrukcji try-finally](../c-language/try-finally-statement-c.md) Aby uzyskać więcej informacji na temat obsługi zakończenia.  
  
```  
.  
.  
.  
puts("hello");  
__try{  
   puts("in try");  
   __try{  
      puts("in try");  
      RAISE_AN_EXCEPTION();  
   }__finally{  
      puts("in finally");  
   }  
}__except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ){  
   puts("in except");  
}  
puts("world");  
```  
  
 Jest to dane wyjściowe w przykładzie z komentarzami dodane po prawej stronie:  
  
```  
hello  
in try              /* fall into try                     */  
in try              /* fall into nested try                */  
in filter           /* execute filter; returns 1 so accept  */  
in finally          /* unwind nested finally                */  
in except           /* transfer control to selected handler */  
world               /* flow out of handler                  */  
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [try-except, instrukcja](../cpp/try-except-statement.md)