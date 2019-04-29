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
ms.openlocfilehash: 9940fdf983f6141c0de207509bb800533b0f1eb8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345815"
---
# <a name="try-except-statement-c"></a>try-except — instrukcja (C)

**Microsoft Specific**

**Spróbuj — z wyjątkiem** instrukcji jest rozszerzeniem firmy Microsoft, język C, który umożliwia aplikacjom przejęcie kontroli nad programem po wystąpieniu zdarzenia, które normalnie zakończyć wykonywania. Takie zdarzenia nazywane są wyjątkami, a mechanizm, który zajmuje się wyjątkami nazywa się strukturalną obsługą wyjątków.

Wyjątki mogą być dowolnego sprzętu lub oprogramowania oparte. Nawet wtedy, gdy aplikacje nie mogą całkowicie odzyskać sprawności po wystąpieniu wyjątku sprzętowego lub programowego, strukturalna obsługa wyjątków umożliwia wyświetlenie informacji o błędzie i pozwala na przechwycenie wewnętrznego stanu aplikacji, aby pomóc w zdiagnozowaniu problemu. Jest to szczególnie użyteczne w przypadku sporadycznych problemów, których nie można łatwo odtworzyć.

## <a name="syntax"></a>Składnia

*instrukcji z wyjątkiem try*: **__try** *compound-statement*  

**__except (** *wyrażenie* **)** *compound-statement* 

Instrukcja złożona po `__try` klauzula jest sekcja chroniona. Złożone wyrażenie po klauzuli `__except` to program obsługi wyjątków. Kod obsługi wyjątku określa zestaw akcji do wykonania, jeśli wyjątek jest zgłaszany podczas wykonywania sekcji chronionej. Wykonanie działa w następujący sposób:

1. Sekcja chroniona jest wykonywana.

1. Jeśli podczas wykonywania sekcji chronionej nie wystąpi wyjątek, program kontynuuje wykonywanie instrukcji po klauzuli `__except`.

1. Jeśli wystąpi wyjątek podczas wykonywania sekcji chronionej lub w dowolnej procedurze, wywołuje sekcję chronioną, `__except` wyrażenie jest obliczane i wartość zwracana określa sposób obsługi wyjątku. Istnieją trzy wartości:

   `EXCEPTION_CONTINUE_SEARCH` Wyjątek nie został rozpoznany. Kontynuuj przeszukiwanie stosu obsługi, najpierw zawierającego wyrażenia **spróbuj — z wyjątkiem** instrukcji, następnie obsługi z następnym największym priorytetem.

   `EXCEPTION_CONTINUE_EXECUTION` Wyjątek został rozpoznany, ale ukryty. Kontynuuj wykonywanie w punkcie, w którym wystąpił wyjątek.

   `EXCEPTION_EXECUTE_HANDLER` Wyjątek został rozpoznany. Kontrola jest przekazywana do programu obsługi wyjątków przez wykonanie `__except` instrukcja złożona (c), a następnie kontynuuj wykonywanie w momencie wystąpienia wyjątku.

Ponieważ `__except` wyrażenie jest obliczane jak wyrażenie C, zatem zostaje ograniczone do pojedynczej wartości, operator wyrażenia warunkowego lub operatora przecinka. Jeśli wymagane jest bardziej rozległe przetwarzanie, wyrażenie może wywołać procedurę, która zwraca jedną z trzech wartości wymienionych powyżej.

> [!NOTE]
>  Strukturalna obsługa wyjątków działa z plikami źródłowymi C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto mechanizm obsługi wyjątków C++ jest bardziej elastyczne, gdyż może obsługiwać wyjątki dowolnego typu.

> [!NOTE]
>  Dla programów C++ Obsługa wyjątków języka C++ powinny być używane zamiast strukturalna Obsługa wyjątków. Aby uzyskać więcej informacji, zobacz [wyjątków](../cpp/exception-handling-in-visual-cpp.md) w *C++ Language Reference*.

Każda procedura w aplikacji może mieć własną obsługę wyjątków. `__except` Wyrażenie wykonuje się w zakresie `__try` treści. Oznacza to, czy ma ona dostęp do żadnych zmiennych lokalnych zadeklarowana.

`__leave` — Słowo kluczowe jest prawidłowy w ramach **spróbuj — z wyjątkiem** blok instrukcji. Efekt `__leave` jest przeskoczenie do końca **spróbuj — z wyjątkiem** bloku. Wznawia wykonanie po zakończeniu obsługi wyjątków. Mimo że `goto` instrukcja może być używana, aby osiągnąć ten sam wynik `goto` instrukcja powoduje odwrócenie stosu. `__leave` Instrukcja jest bardziej wydajne, ponieważ nie wymaga wykonywania operacji odwijania stosu.

Kończenie **spróbuj — z wyjątkiem** przy użyciu instrukcji `longjmp` funkcji środowiska uruchomieniowego jest uznawany za Nienormalne zakończenie. Nie jest dozwolone realizowanie `__try` instrukcji, ale informacje prawne wyjście z niej. Obsługa wyjątków nie jest wywoływana, gdy proces jest zabita w środku wykonywania wyrażenia **spróbuj — z wyjątkiem** instrukcji.

## <a name="example"></a>Przykład

Poniżej przedstawiono przykład do obsługi wyjątku i programu obsługi zakończenia. Zobacz [instrukcji try-finally](../c-language/try-finally-statement-c.md) Aby uzyskać więcej informacji na temat obsługi zakończenia.

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

Oto dane wyjściowe z przykładu, z komentarzem dodane po prawej stronie:

```
hello
in try              /* fall into try                     */
in try              /* fall into nested try                */
in filter           /* execute filter; returns 1 so accept  */
in finally          /* unwind nested finally                */
in except           /* transfer control to selected handler */
world               /* flow out of handler                  */
```

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[try-except, instrukcja](../cpp/try-except-statement.md)
