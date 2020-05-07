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

Instrukcja **try-except** jest rozszerzeniem firmy Microsoft do języka C, który umożliwia aplikacjom uzyskanie kontroli nad programem, gdy wystąpią zdarzenia, które normalnie kończą wykonywanie. Takie zdarzenia nazywane są wyjątkami, a mechanizm, który zajmuje się wyjątkami nazywa się strukturalną obsługą wyjątków.

Wyjątki mogą być zależne od sprzętu lub oprogramowania. Nawet wtedy, gdy aplikacje nie mogą całkowicie odzyskać sprawności po wystąpieniu wyjątku sprzętowego lub programowego, strukturalna obsługa wyjątków umożliwia wyświetlenie informacji o błędzie i pozwala na przechwycenie wewnętrznego stanu aplikacji, aby pomóc w zdiagnozowaniu problemu. Jest to szczególnie użyteczne w przypadku sporadycznych problemów, których nie można łatwo odtworzyć.

## <a name="syntax"></a>Składnia

*try-except-Statement*: **__try**  *złożonej instrukcji*

*instrukcja złożonej instrukcji* **__except (***Expression***)**      

Instrukcja złożona po `__try` klauzuli jest sekcją chronioną. Złożone wyrażenie po klauzuli `__except` to program obsługi wyjątków. Program obsługi określa zestaw akcji do wykonania, jeśli wyjątek jest wywoływany podczas wykonywania sekcji chronionej. Wykonanie przebiega w następujący sposób:

1. Sekcja chroniona jest wykonywana.

1. Jeśli podczas wykonywania sekcji chronionej nie wystąpi wyjątek, program kontynuuje wykonywanie instrukcji po klauzuli `__except`.

1. Jeśli wystąpi wyjątek podczas wykonywania sekcji chronionej lub w każdej rutynowych wywołaniach sekcji chronionej, `__except` wyrażenie jest oceniane i zwracana wartość określa sposób obsługi wyjątku. Istnieją trzy wartości:

   `EXCEPTION_CONTINUE_SEARCH`Wyjątek nie został rozpoznany. Kontynuuj wyszukiwanie stosu dla programu obsługi, najpierw dla zawiera instrukcje **try-except** , a następnie dla programów obsługi przy użyciu następnego najwyższego pierwszeństwa.

   `EXCEPTION_CONTINUE_EXECUTION`Wyjątek jest rozpoznawany, ale odrzucony. Kontynuuj wykonywanie w punkcie, w którym wystąpił wyjątek.

   `EXCEPTION_EXECUTE_HANDLER`Wyjątek jest rozpoznawany. Przetransferuj formant do programu obsługi wyjątków, `__except` wykonując instrukcję złożoną, a następnie kontynuuj wykonywanie w punkcie, w którym wystąpił wyjątek.

Ponieważ `__except` wyrażenie jest oceniane jako wyrażenie C, jest ograniczone do pojedynczej wartości, operatora warunkowego wyrażenia lub operatora przecinka. Jeśli wymagane jest bardziej rozległe przetwarzanie, wyrażenie może wywołać procedurę, która zwraca jedną z trzech wartości wymienionych powyżej.

> [!NOTE]
> Strukturalna obsługa wyjątków współpracuje z plikami źródłowymi C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto mechanizm obsługi wyjątków C++ jest znacznie bardziej elastyczny, dzięki czemu może obsługiwać wyjątki dowolnego typu.

> [!NOTE]
> W przypadku programów C++, obsługa wyjątków C++ powinna być używana zamiast strukturalnej obsługi wyjątków. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md) w *dokumentacji języka C++*.

Każda procedura w aplikacji może mieć własny program obsługi wyjątków. Wyrażenie `__except` jest wykonywane w zakresie `__try` treści. Oznacza to, że ma dostęp do wszelkich zmiennych lokalnych zadeklarowanych w tym miejscu.

`__leave` Słowo kluczowe jest prawidłowe w bloku instrukcji **try-except** . Efekt `__leave` ma przeskoczyć do końca bloku **try-except** . Wykonywanie zostało wznowione po zakończeniu obsługi wyjątków. Mimo że `goto` instrukcja może służyć do osiągnięcia tego samego wyniku, `goto` instrukcja powoduje odwinięcie stosu. Instrukcja `__leave` jest wydajniejsza, ponieważ nie obejmuje odwinięcia stosu.

Opuszczanie instrukcji **try-except** przy użyciu funkcji `longjmp` Run-Time jest uznawane za nietypowe zakończenie. Przechodzenie do `__try` instrukcji nie jest dozwolone, ale istnieje możliwość wychodzenia z jednego. Procedura obsługi wyjątków nie jest wywoływana, jeśli proces zostanie zamknięty w trakcie wykonywania instrukcji **try-except** .

## <a name="example"></a>Przykład

Poniżej znajduje się przykład obsługi wyjątków i procedury obsługi zakończenia. Aby uzyskać więcej informacji na temat programów obsługi zakończenia [, zobacz instrukcję try-finally](../c-language/try-finally-statement-c.md) .

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

Jest to wynik z przykładu, z dodaniem komentarza po prawej stronie:

```
hello
in try              /* fall into try                     */
in try              /* fall into nested try                */
in filter           /* execute filter; returns 1 so accept  */
in finally          /* unwind nested finally                */
in except           /* transfer control to selected handler */
world               /* flow out of handler                  */
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[try-except, instrukcja](../cpp/try-except-statement.md)
