---
title: Instrukcja try-finally | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df3519cac370ac7595e0789eeab43c6488120fc8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024245"
---
# <a name="try-finally-statement"></a>try-finally — instrukcja

**Microsoft Specific**

Następująca składnia opisuje **try-finally** instrukcji:

```cpp
__try {
   // guarded code
}
__finally {
   // termination code
}
```

## <a name="grammar"></a>Gramatyka

*Spróbuj na koniec instrukcji*: **__try** *compound-statement*

**__finally** *compound-statement*

**Try-finally** instrukcja jest rozszerzeniem firmy Microsoft do języków C i C++, które umożliwiają aplikacji docelowej, co gwarantuje wykonywanie czyszczenia kodu, gdy działanie zostanie zakłócone wykonanie bloku kodu. Oczyszczanie składa się z zadania, takie jak cofanie przydziału pamięci, zamykanie plików i zwalniania dojścia do plików. **Try-finally** instrukcji jest szczególnie przydatne dla procedur, które mają w kilku miejscach, w którym dokonuje błędu, który może spowodować przedwczesne zwracają rutynowych.

Aby uzyskać powiązane informacje i przykładowy kod, zobacz [spróbuj-except, instrukcja](../cpp/try-except-statement.md). Aby uzyskać więcej informacji na temat ogólnie rzecz biorąc obsługi wyjątków strukturalnych, zobacz [obsługi wyjątków strukturalnych](../cpp/structured-exception-handling-c-cpp.md). Aby uzyskać więcej informacji na temat obsługi wyjątków w aplikacji zarządzanych, zobacz [obsługi wyjątków w ramach/CLR](../windows/exception-handling-cpp-component-extensions.md).

> [!NOTE]
>  Strukturalna obsługa wyjątków działa z Win32 dla plików źródłowych C i C++. Jednakże nie jest specjalnie zaprojektowana dla języka C++. Można zapewnić, że kod będzie bardziej przenośny przy użyciu obsługi wyjątków C++. Ponadto, obsługa wyjątków C++ jest bardziej elastyczna, gdyż może obsługiwać wyjątki dowolnego typu. Programy w języku C++, zalecane jest używanie mechanizmu obsługi wyjątków C++ ([try, catch i throw](../cpp/try-throw-and-catch-statements-cpp.md) instrukcji).

Instrukcja złożona po **__try** klauzula jest sekcja chroniona. Instrukcja złożona po **__finally** klauzula jest programu obsługi zakończenia. Kod obsługi wyjątku określa zestaw akcji, które są wykonywane, gdy sekcja chroniona jest został zakończony, niezależnie od tego, czy sekcja chroniona jest został zakończony przez wyjątek (Nienormalne zakończenie) lub standardowy poniżej (normalne zakończenie).

Kontrola osiąga **__try** oświadczenie proste wykonywania sekwencyjnego (poniżej). Kiedy sterowania przechodzi **__try**, jego skojarzony program obsługi stanie się aktywny. Jeśli przepływ sterowania osiągnie koniec bloku try, wykonanie działa w następujący sposób:

1. Program obsługi przerwania jest wywoływana.

1. Po zakończeniu działania programu obsługi zakończenia, wykonywanie jest kontynuowane po **__finally** instrukcji. Niezależnie od tego, jak chronionych sekcji kończy się (na przykład za pośrednictwem **goto** z treści chronionych lub **zwracają** instrukcji), program obsługi przerwania jest wykonywany *przed* Przenosi przepływ sterowania poza sekcję chronioną.

     A **__finally** instrukcji nie blokuje wyszukiwanie obsługi odpowiednich wyjątków.

Jeśli wystąpi wyjątek w **__try** bloku, system operacyjny musi odnaleźć program obsługi wyjątku lub program zakończy się niepowodzeniem. Jeśli program obsługi zostanie znaleziony, wszystkie **__finally** bloki są wykonywane i wykonanie zostanie wznowione w obsłudze.

Załóżmy na przykład, serii wywołań funkcji łącza funkcji A działać D, jak pokazano na poniższej ilustracji. Każda funkcja ma jednego programu obsługi zakończenia. Jeśli wyjątek jest zgłaszany w funkcji D i obsłużony a, programy obsługi zakończenia są nazywane w podanej kolejności, jak system rozwija stos: D, C, B.

![Kolejność zakończenia&#45;wykonanie procedury obsługi](../cpp/media/vc38cx1.gif "vc38CX1") kolejność wykonywania programu obsługi zakończenia

> [!NOTE]
>  Zachowanie try-finally, różni się od innych języków, które obsługują korzystanie z **na koniec**, takich jak C#.  Pojedynczy **__try** może znajdować albo, ale nie oba **__finally** i **__except**.  Jeśli oba mają być używane razem, spróbuj zewnętrznym — z wyjątkiem instrukcji należy ująć wewnętrznej instrukcji try-finally.  Reguły, określając podczas każdego bloku wykonuje też są różne.

## <a name="the-leave-keyword"></a>Słowo kluczowe __leave

**__Leave** — słowo kluczowe jest prawidłowy tylko wewnątrz sekcji chronionej **try-finally** instrukcji, a jego efektem jest przeskoczenie do końca sekcji chronionej. Wykonywanie jest kontynuowane po pierwszej instrukcji w programu obsługi zakończenia.

A **goto** instrukcji może również przeskoczyć poza sekcję chronioną, ale obniża wydajność, ponieważ wywołuje, wykonywania operacji odwijania stosu. **__Leave** instrukcja jest bardziej wydajne, ponieważ nie powoduje odwrócenie stosu.

## <a name="abnormal-termination"></a>Nienormalne zakończenie

Kończenie **try-finally** przy użyciu instrukcji [longjmp](../c-runtime-library/reference/longjmp.md) funkcji środowiska uruchomieniowego jest uznawany za Nienormalne zakończenie. Nie jest dozwolone realizowanie **__try** instrukcji, ale informacje prawne wyjście z niej. Wszystkie **__finally** instrukcji, które są aktywni w okresie między punktem wyjścia (normalne zakończenie programu **__try** bloku) i miejscu docelowym ( **__except** blokowania, obsługuje wyjątek) muszą być uruchamiane. Jest to rozwinięcie lokalne.

Jeśli **spróbuj** bloku przedwcześnie z jakiegokolwiek powodu, w tym skoku poza blok, system wykonuje skojarzonego **na koniec** bloku jako część procesu odwijania stosu. W takich przypadkach [AbnormalTermination](/windows/desktop/Debug/abnormaltermination) funkcja zwraca **true** Jeśli wywoływana z poziomu **na koniec** zablokować; w przeciwnym razie zwraca **false**.

Program obsługi przerwania nie jest wywoływana, gdy proces jest zabita w środku wykonywania wyrażenia **try-finally** instrukcji.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Pisanie programu obsługi zakończenia](../cpp/writing-a-termination-handler.md)<br/>
[Obsługa wyjątków strukturalnych (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[Składnia programu obsługi zakończenia](/windows/desktop/Debug/termination-handler-syntax)