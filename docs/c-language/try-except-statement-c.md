---
title: try-except — instrukcja (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
ms.openlocfilehash: 2ca5299a5ab20b8985a520f25bb654ead0c25e2b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349740"
---
# <a name="try-except-statement-c"></a>try-except — instrukcja (C)

**Specyficzne dla firmy Microsoft**

**Instrukcja try-except** jest rozszerzeniem firmy Microsoft do języka C, który umożliwia aplikacjom przejęcie kontroli nad programem, gdy wystąpią zdarzenia, które zwykle kończą wykonywanie. Takie zdarzenia nazywane są wyjątkami, a mechanizm, który zajmuje się wyjątkami nazywa się strukturalną obsługą wyjątków.

Wyjątki mogą być oparte na sprzęcie lub oprogramowaniu. Nawet wtedy, gdy aplikacje nie mogą całkowicie odzyskać sprawności po wystąpieniu wyjątku sprzętowego lub programowego, strukturalna obsługa wyjątków umożliwia wyświetlenie informacji o błędzie i pozwala na przechwycenie wewnętrznego stanu aplikacji, aby pomóc w zdiagnozowaniu problemu. Jest to szczególnie użyteczne w przypadku sporadycznych problemów, których nie można łatwo odtworzyć.

## <a name="syntax"></a>Składnia

*try-except-statement*: **__try**  *zestawienie złożone*

**__except (**  *wyrażenie*  **)**  *złożona instrukcja*

Instrukcja złożona `__try` po klauzuli jest sekcją chroniona. Złożone wyrażenie po klauzuli `__except` to program obsługi wyjątków. Program obsługi określa zestaw akcji, które należy podjąć, jeśli wyjątek jest zgłaszany podczas wykonywania sekcji strzeżonej. Wykonanie przebiega w następujący sposób:

1. Sekcja chroniona jest wykonywana.

1. Jeśli podczas wykonywania sekcji chronionej nie wystąpi wyjątek, program kontynuuje wykonywanie instrukcji po klauzuli `__except`.

1. Jeśli wyjątek występuje podczas wykonywania sekcji chronionej lub w dowolnej `__except` procedury wywołania sekcji chronionej, wyrażenie jest oceniane i zwracana wartość określa sposób obsługi wyjątku. Istnieją trzy wartości:

   `EXCEPTION_CONTINUE_SEARCH`Wyjątek nie jest rozpoznawany. Kontynuuj wyszukiwanie stosu dla programu obsługi, najpierw dla zawierające **try-except** instrukcji, a następnie dla programów obsługi z następnego najwyższego pierwszeństwa.

   `EXCEPTION_CONTINUE_EXECUTION`Wyjątek jest rozpoznawany, ale odrzucany. Kontynuuj wykonywanie w punkcie, w którym wystąpił wyjątek.

   `EXCEPTION_EXECUTE_HANDLER`Wyjątek jest rozpoznawany. Przenieś kontrolę do obsługi wyjątków, wykonując instrukcję złożoną, `__except` a następnie kontynuuj wykonywanie w punkcie, w którego wystąpił wyjątek.

Ponieważ `__except` wyrażenie jest oceniane jako wyrażenie C, jest ograniczone do pojedynczej wartości, operatora wyrażenia warunkowego lub operatora przecinka. Jeśli wymagane jest bardziej rozległe przetwarzanie, wyrażenie może wywołać procedurę, która zwraca jedną z trzech wartości wymienionych powyżej.

> [!NOTE]
> Obsługa wyjątków strukturalnych działa z plikami źródłowymi języka C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto mechanizm obsługi wyjątków C++ jest znacznie bardziej elastyczny, ponieważ może obsługiwać wyjątki dowolnego typu.

> [!NOTE]
> W przypadku programów C++ należy używać obsługi wyjątków języka C++ zamiast obsługi wyjątków strukturalnych. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md) w *odwołaniu do języka języka języka C++*.

Każda procedura w aplikacji może mieć swój własny program obsługi wyjątków. Wyrażenie `__except` jest wykonywane w zakresie `__try` treści. Oznacza to, że ma dostęp do wszystkich zmiennych lokalnych zadeklarowanych tam.

Słowo `__leave` kluczowe jest prawidłowe w bloku instrukcji **try-except.** Efektem `__leave` jest, aby przejść do końca **try-except** bloku. Wykonywanie wznawia po zakończeniu obsługi wyjątków. Chociaż `goto` instrukcja może służyć do osiągnięcia `goto` tego samego wyniku, instrukcja powoduje odwijania stosu. Instrukcja `__leave` jest bardziej wydajne, ponieważ nie obejmuje odwijania stosu.

Zamykanie **instrukcji try-except** `longjmp` przy użyciu funkcji czasu wykonywania jest uważane za nieprawidłowe zakończenie. To jest nielegalne, `__try` aby przejść do oświadczenia, ale legalne wyskoczyć z jednego. Program obsługi wyjątków nie jest wywoływana, jeśli proces zostanie zabity w trakcie wykonywania **instrukcji try-except.**

## <a name="example"></a>Przykład

Poniżej przedstawiono przykład obsługi wyjątków i obsługi zakończenia. Zobacz [instrukcja try-finally, aby](../c-language/try-finally-statement-c.md) uzyskać więcej informacji na temat obsługi zakończenia.

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

Jest to wynik z przykładu, z komentarzem dodanym po prawej stronie:

```
hello
in try              /* fall into try                     */
in try              /* fall into nested try                */
in filter           /* execute filter; returns 1 so accept  */
in finally          /* unwind nested finally                */
in except           /* transfer control to selected handler */
world               /* flow out of handler                  */
```

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[try-except, instrukcja](../cpp/try-except-statement.md)
