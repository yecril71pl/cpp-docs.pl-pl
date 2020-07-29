---
title: 'Wyjątki: konwertowanie z makr wyjątków MFC'
ms.date: 08/27/2018
helpviewer_keywords:
- converting exceptions [MFC]
- exception objects [MFC]
- conversions [MFC], code written with MFC macros
- keywords [MFC], macros
- macrosv, C++ keywords
- exception objects [MFC], deleting
- CException class [MFC], deleting CException class objects
- exceptions [MFC], converting
- exceptions [MFC], deleting exception objects
- catch blocks [MFC], delimiting
- exception handling [MFC], converting exceptions
ms.assetid: bd3ac3b3-f3ce-4fdd-a168-a2cff13ed796
ms.openlocfilehash: e8e7f47b66f4263ed55d73c0aac1fda73d72393c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87183815"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Wyjątki: konwertowanie z makr wyjątków MFC

To jest zaawansowany temat.

W tym artykule wyjaśniono, jak przekonwertować istniejący kod zapisany przy użyciu makr klas Microsoft Foundation — **Wypróbuj**, **catch**, **throw**itd., aby użyć słów kluczowych obsługi wyjątków języka C++ **`try`** , **`catch`** i **`throw`** . Tematy obejmują:

- [Zalety konwersji](#_core_advantages_of_converting)

- [Konwertowanie kodu z makrami wyjątków w celu używania wyjątków C++](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a>Zalety konwersji

Prawdopodobnie nie trzeba konwertować istniejącego kodu, chociaż należy pamiętać o różnicach między implementacjami makr w MFC w wersji 3,0 i implementacjami we wcześniejszych wersjach. Te różnice i kolejne zmiany w zachowaniu kodu zostały omówione w [wyjątkach: zmiany w makrach wyjątków w wersji 3,0](exceptions-changes-to-exception-macros-in-version-3-0.md).

Główne zalety konwersji to:

- Kod, który używa słów kluczowych obsługi wyjątków C++ kompiluje się do nieco mniejszych. EXE lub. Bibliotece.

- Słowa kluczowe obsługi wyjątków C++ są bardziej uniwersalne: mogą obsługiwać wyjątki dowolnego typu danych, które można skopiować ( **`int`** ,,, itd **`float`** **`char`** .), podczas gdy makra obsługują wyjątki tylko dla klas `CException` i klas pochodzących od niej.

Główna różnica między makrami i słowami kluczowymi polega na tym, że kod korzystający z makr "automatycznie" usuwa przechwycony wyjątek, gdy wyjątek wykracza poza zakres. Kod używający słów kluczowych nie, dlatego należy jawnie usunąć przechwycony wyjątek. Aby uzyskać więcej informacji, zobacz [wyjątki artykułów: Przechwytywanie i usuwanie wyjątków](exceptions-catching-and-deleting-exceptions.md).

Kolejną różnicą jest składnia. Składnia makr i słów kluczowych różni się w trzech aspektach:

1. Argumenty makr i deklaracje wyjątku:

   Wywołanie makra **catch** ma następującą składnię:

   **Catch (** *exception_class*, *exception_object_pointer_name* **)**

   Zauważ przecinek między nazwą klasy a nazwą wskaźnika obiektu.

   Deklaracja wyjątku dla **`catch`** słowa kluczowego używa następującej składni:

   **catch (** *exception_type* *exception_name* **)**

   Ta instrukcja deklaracji wyjątku wskazuje typ wyjątku obsługiwanego przez blok catch.

2. Ogranicznik bloków catch:

   Makra, makro **catch** (z argumentami) rozpoczyna pierwszy blok catch; makro **AND_CATCH** rozpoczyna kolejne bloki catch, a makro **END_CATCH** przerywa sekwencję catch.

   Słowa kluczowe, **`catch`** słowo kluczowe (z deklaracją wyjątku) rozpoczyna każdy blok catch. Nie ma żadnego odpowiednika dla makra **END_CATCH** ; blok catch zostaje zakończony zamykającym nawiasem klamrowym.

3. Wyrażenie throw:

   Makra używają **THROW_LAST** , aby ponownie zgłosić bieżący wyjątek. **`throw`** Słowo kluczowe bez argumentu ma ten sam efekt.

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a>Wykonywanie konwersji

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Aby skonwertować kod przy użyciu makr, aby użyć słów kluczowych obsługi wyjątków C++

1. Znajdź wszystkie wystąpienia makr MFC **try**, **catch**, **AND_CATCH**, **END_CATCH**, **throw**i **THROW_LAST**.

2. Zamień lub Usuń wszystkie wystąpienia następujących makr:

   **Wypróbuj** (zamień ją na **`try`** )

   **Catch** (zamień ją na **`catch`** )

   **AND_CATCH** (zastąp go **`catch`** )

   **END_CATCH** (Usuń)

   **Throw** (zamień je na **`throw`** )

   **THROW_LAST** (zastąp go **`throw`** )

3. Zmodyfikuj argumenty makr tak, aby były one zgodne z prawidłowymi deklaracjami wyjątku.

   Na przykład zmień

   [!code-cpp[NVC_MFCExceptions#6](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   na

   [!code-cpp[NVC_MFCExceptions#7](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. Zmodyfikuj kod w blokach catch, aby usunąć obiekty wyjątków stosownie do potrzeb. Aby uzyskać więcej informacji, zobacz [wyjątki artykułów: Przechwytywanie i usuwanie wyjątków](exceptions-catching-and-deleting-exceptions.md).

Oto przykład kodu obsługi wyjątków przy użyciu makr wyjątków MFC. Należy zauważyć, że ponieważ kod w poniższym przykładzie używa makr, wyjątek `e` jest usuwany automatycznie:

[!code-cpp[NVC_MFCExceptions#8](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

Kod w następnym przykładzie używa słów kluczowych wyjątków języka C++, więc wyjątek musi zostać jawnie usunięty:

[!code-cpp[NVC_MFCExceptions#9](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

Aby uzyskać więcej informacji, zobacz [wyjątki: używanie makr MFC i wyjątków C++](exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](exception-handling-in-mfc.md)<br/>
