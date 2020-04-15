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
ms.openlocfilehash: 330f66b1f46542082637645ad53da016b434d4a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372017"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Wyjątki: konwertowanie z makr wyjątków MFC

Jest to zaawansowany temat.

W tym artykule wyjaśniono, jak przekonwertować istniejący kod napisany za pomocą makr Microsoft Foundation Class — **TRY,** **CATCH**, **THROW**i tak dalej — aby użyć słów kluczowych obsługi wyjątków C++, **spróbuj**, **złapać**i **wrzucić**. Tematy obejmują:

- [Korzyści z konwersji](#_core_advantages_of_converting)

- [Konwertowanie kodu z makrami wyjątków w celu używania wyjątków języka C++](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a>Zalety konwersji

Prawdopodobnie nie trzeba konwertować istniejącego kodu, chociaż należy pamiętać o różnicach między implementacjami makr w wersji MFC 3.0 i implementacjami we wcześniejszych wersjach. Te różnice i kolejne zmiany w zachowaniu kodu są omówione w [wyjątki: Zmiany makr wyjątków w wersji 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).

Główne zalety konwersji to:

- Kod, który używa słów kluczowych obsługi wyjątków C++ kompiluje się do nieco mniejszego . EXE lub . Dll.

- Słowa kluczowe obsługi wyjątków języka C++ są bardziej wszechstronne: mogą obsługiwać wyjątki dowolnego typu danych, które mogą być kopiowane **(int** `CException` , **float**, **char**i tak dalej), podczas gdy makra obsługują wyjątki tylko klasy i klasy pochodzące z niego.

Główną różnicą między makrami a słowami kluczowymi jest to, że kod przy użyciu makr "automatycznie" usuwa przechwycony wyjątek, gdy wyjątek wykracza poza zakres. Kod przy użyciu słów kluczowych nie, więc należy jawnie usunąć przechwycony wyjątek. Aby uzyskać więcej informacji, zobacz artykuł [Wyjątki: Przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md).

Inną różnicą jest składnia. Składnia makr i słów kluczowych różni się pod trzema względami:

1. Argumenty makr i deklaracje wyjątków:

   Wywołanie makr **CATCH** ma następującą składnię:

   **CATCH(** *exception_class*, *exception_object_pointer_name* **)**

   Zwróć uwagę na przecinek między nazwą klasy a nazwą wskaźnika obiektu.

   Deklaracja **wyjątku** dla catch słowa kluczowego używa tej składni:

   **exception_type** *exception_type* *exception_name* **)**

   Ta instrukcja deklaracji wyjątku wskazuje typ wyjątku uchwyty bloku catch.

2. Rozgraniczenie bloków połowowych:

   W makrach makr **CATCH** (z jego argumentami) rozpoczyna pierwszy blok catch; **makro AND_CATCH** rozpoczyna kolejne bloki catch, a makro **END_CATCH** kończy sekwencję bloków catch.

   W przypadku słów kluczowych **catch** słowo kluczowe (z jego deklaracją wyjątków) rozpoczyna się każdy blok catch. Nie ma odpowiednika **END_CATCH** makra; blok zaczepu kończy się nawiasem klamrowym zamykającym.

3. Wyrażenie throw:

   Makra używają **THROW_LAST** do ponownego zgłaszania bieżącego wyjątku. Słowo kluczowe **throw,** bez argumentu, ma ten sam efekt.

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a>Konwersja

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Aby przekonwertować kod przy użyciu makr do używania słów kluczowych obsługi wyjątków języka C++

1. Zlokalizuj wszystkie wystąpienia makr MFC **TRY**, **CATCH**, **AND_CATCH**, **END_CATCH**, **THROW**i **THROW_LAST**.

2. Zastąp lub usuń wszystkie wystąpienia następujących makr:

   **TRY** (Zamień go **na try)**

   **CATCH** (Wymień go **na haczyk)**

   **AND_CATCH** (Wymień go **na haczyk)**

   **END_CATCH** (Usuń)

   **THROW** (Wymień go **na throw)**

   **THROW_LAST** (Wymień go **na rzut)**

3. Zmodyfikuj argumenty makra, tak aby tworzyły prawidłowe deklaracje wyjątków.

   Na przykład zmień

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   na

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. Zmodyfikuj kod w blokach catch, tak aby usuwał obiekty wyjątków w razie potrzeby. Aby uzyskać więcej informacji, zobacz artykuł [Wyjątki: Przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md).

Oto przykład kodu obsługi wyjątków przy użyciu makr wyjątków MFC. Należy zauważyć, że ponieważ kod w poniższym przykładzie używa makr, wyjątek `e` jest usuwany automatycznie:

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

Kod w następnym przykładzie używa słów kluczowych wyjątku C++, więc wyjątek musi zostać jawnie usunięty:

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

Aby uzyskać więcej informacji, zobacz [Wyjątki: Używanie makr MFC i wyjątków C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="see-also"></a>Zobacz też

[Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)<br/>
