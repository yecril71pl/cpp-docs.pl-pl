---
title: try-except, instrukcja (C)
description: Microsoft C/C++ implementuje obsługę wyjątków strukturalnych (SEH) przy użyciu rozszerzenia języka instrukcji try-except.
ms.date: 08/24/2020
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
ms.openlocfilehash: e327150431fef3384f2b98940939444b2e6d96ea
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898722"
---
# <a name="try-except-statement-c"></a>try-except, instrukcja (C)

**specyficzne dla firmy Microsoft**

`try-except`Instrukcja to rozszerzenie firmy Microsoft do języka C, który umożliwia aplikacjom uzyskanie kontroli nad programem, gdy wystąpią zdarzenia, które normalnie kończą wykonywanie. Takie zdarzenia nazywane są wyjątkami, a mechanizm, który zajmuje się wyjątkami nazywa się strukturalną obsługą wyjątków.

Wyjątki mogą być zależne od sprzętu lub oprogramowania. Nawet w przypadku, gdy aplikacje nie mogą całkowicie odzyskać sprawności przed wyjątkami sprzętowymi i programowymi, strukturalna obsługa wyjątków umożliwia rejestrowanie i wyświetlanie informacji o błędach. Warto zastanowić się, że w celu ułatwienia zdiagnozowania problemu jest zalewkowany wewnętrzny stan aplikacji. W szczególności pomocne jest nieprzerwane Rozwiązywanie problemów, które nie są łatwe do odtworzenia.

## <a name="syntax"></a>Składnia

> *`try-except-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__except (`**  *`expression`*  **`)`** *`compound-statement`*

Instrukcja złożona po **`__try`** klauzuli jest *sekcją chronioną*. Instrukcja złożona po **`__except`** klauzuli jest *programem obsługi wyjątków*. Procedura obsługi określa zestaw akcji do wykonania, jeśli wyjątek jest wywoływany podczas wykonywania sekcji chronionej. Wykonanie przebiega w następujący sposób:

1. Sekcja chroniona jest wykonywana.

1. Jeśli podczas wykonywania sekcji chronionej nie wystąpi wyjątek, wykonanie kontynuuje się w instrukcji po **`__except`** klauzuli.

1. Jeśli podczas wykonywania sekcji chronionej wystąpi wyjątek lub w każdej z rutynowych wywołań sekcji chronionej, **`__except`** wyrażenie zostanie obliczone. Zwracana wartość określa sposób obsługi wyjątku. Możliwe są trzy wartości:

   - `EXCEPTION_CONTINUE_SEARCH`: Wyjątek nie został rozpoznany. Kontynuuj wyszukiwanie stosu dla programu obsługi, najpierw dla zawierających `try-except` instrukcje, a następnie dla programów obsługi przy użyciu następnego najwyższego pierwszeństwa.

   - `EXCEPTION_CONTINUE_EXECUTION`: Wyjątek jest rozpoznawany, ale odrzucony. Kontynuuj wykonywanie w punkcie, w którym wystąpił wyjątek.

   - `EXCEPTION_EXECUTE_HANDLER` Wyjątek jest rozpoznawany. Przetransferuj formant do programu obsługi wyjątków **`__except`** , wykonując instrukcję złożoną, a następnie kontynuuj wykonywanie w punkcie, w którym wystąpił wyjątek.

Ponieważ **`__except`** wyrażenie jest oceniane jako wyrażenie C, jest ograniczone do pojedynczej wartości, operatora warunkowego wyrażenia lub operatora przecinka. Jeśli wymagane jest bardziej rozległe przetwarzanie, wyrażenie może wywołać procedurę, która zwraca jedną z trzech wartości wymienionych powyżej.

> [!NOTE]
> Strukturalna obsługa wyjątków współpracuje z plikami źródłowymi C i C++. Nie jest to jednak przeznaczone specjalnie dla języka C++. W przypadku przenośnych programów C++ obsługa wyjątków C++ powinna być używana zamiast strukturalnej obsługi wyjątków. Ponadto mechanizm obsługi wyjątków C++ jest znacznie bardziej elastyczny, dzięki czemu może obsługiwać wyjątki dowolnego typu. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków](../cpp/exception-handling-in-visual-cpp.md) w *dokumentacji języka C++*.

Każda procedura w aplikacji może mieć własny program obsługi wyjątków. **`__except`** Wyrażenie jest wykonywane w zakresie **`__try`** treści. Ma dostęp do wszystkich zmiennych lokalnych zadeklarowanych w tym miejscu.

**`__leave`** Słowo kluczowe jest prawidłowe w `try-except` bloku instrukcji. Efekt **`__leave`** ma przeskoczyć do końca `try-except` bloku. Wykonywanie zostało wznowione po zakończeniu obsługi wyjątków. Mimo że **`goto`** instrukcja może służyć do osiągnięcia tego samego wyniku, **`goto`** instrukcja powoduje odwinięcie stosu. **`__leave`** Instrukcja jest bardziej wydajna, ponieważ nie obejmuje odwinięcia stosu.

Kończenie `try-except` instrukcji przy użyciu `longjmp` funkcji run-time jest uznawane za nietypowe zakończenie. Nie jest to dozwolone, aby przechodzić do **`__try`** instrukcji, ale jest to dozwolone w przypadku przechodzenia z jednego. Procedura obsługi wyjątków nie jest wywoływana, jeśli proces zostanie zamknięty w trakcie wykonywania `try-except` instrukcji.

## <a name="example"></a>Przykład

Oto przykład procedury obsługi wyjątków i procedury obsługi zakończenia. Aby uzyskać więcej informacji na temat programów obsługi zakończenia, zobacz [ `try-finally` instrukcja (C)](../c-language/try-finally-statement-c.md).

```C
.
.
.
puts("hello");
__try {
   puts("in try");
   __try {
      puts("in try");
      RAISE_AN_EXCEPTION();
   } __finally {
      puts("in finally");
   }
} __except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ) {
   puts("in except");
}
puts("world");
```

Oto dane wyjściowe z przykładu z komentarzem dodany po prawej stronie:

```Output
hello
in try              /* fall into try                        */
in try              /* fall into nested try                 */
in filter           /* execute filter; returns 1 so accept  */
in finally          /* unwind nested finally                */
in except           /* transfer control to selected handler */
world               /* flow out of handler                  */
```

**ZAKOŃCZENIE specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[`try-except` Instrukcja (C++)](../cpp/try-except-statement.md)
