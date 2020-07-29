---
title: 'Wyjątki: używanie makr MFC i wyjątków języka C++'
ms.date: 11/04/2016
helpviewer_keywords:
- exception objects [MFC]
- memory leaks [MFC], exception object not deleted
- exception handling [MFC], MFC
- try-catch exception handling [MFC], mixing MFC macros and C++ keywords
- exception objects [MFC], deleting
- exceptions [MFC], MFC macros vs. C++ keywords
- catch blocks [MFC], mixed
- exception handling [MFC], mixed-language
- nested try blocks [MFC]
- catch blocks [MFC], explicitly deleting code in
- try-catch exception handling [MFC], nested try blocks
- heap corruption [MFC]
- nested catch blocks [MFC]
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
ms.openlocfilehash: 9e97eb545dedd3ac38dd93471f82aecc382717ae
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223177"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Wyjątki: używanie makr MFC i wyjątków języka C++

W tym artykule opisano zagadnienia dotyczące pisania kodu, który używa makr obsługi wyjątków MFC i słów kluczowych obsługi wyjątków C++.

W tym artykule omówiono następujące tematy:

- [Mieszanie słów kluczowych wyjątków i makr](#_core_mixing_exception_keywords_and_macros)

- [Wypróbuj bloki wewnątrz bloków catch](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a>Mieszanie słów kluczowych wyjątków i makr

Można mieszać makra wyjątków MFC i słowa kluczowe wyjątków C++ w tym samym programie. Ale nie można mieszać makr MFC ze słowami kluczowymi wyjątków C++ w tym samym bloku, ponieważ makra usuwają obiekty wyjątków automatycznie, gdy wykraczają poza zakres, natomiast kod używający słów kluczowych obsługujących wyjątek nie. Aby uzyskać więcej informacji, zobacz [wyjątki artykułów: Przechwytywanie i usuwanie wyjątków](exceptions-catching-and-deleting-exceptions.md).

Główna różnica między makrami i słowami kluczowymi polega na tym, że makra "automatycznie" usuwają przechwycony wyjątek, gdy wyjątek wykracza poza zakres. Kod używający słów kluczowych nie; wyjątki przechwycone w bloku catch muszą zostać jawnie usunięte. Mieszanie makr i słów kluczowych wyjątków języka C++ może spowodować przecieki pamięci, gdy obiekt wyjątku nie został usunięty lub uszkodzenie sterty po dwukrotnym usunięciu wyjątku.

Poniższy kod, na przykład unieważnia wskaźnik wyjątku:

[!code-cpp[NVC_MFCExceptions#10](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

Problem występuje, ponieważ `e` jest usuwany po zakończeniu wykonywania z bloku **catch** "wewnętrzny". Użycie makra **THROW_LAST** zamiast instrukcji **throw** spowoduje, że blok "zewnętrzny" **przechwytuje** prawidłowy wskaźnik:

[!code-cpp[NVC_MFCExceptions#11](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a>Wypróbuj bloki wewnątrz bloków catch

Nie można ponownie zgłosić bieżącego wyjątku z **`try`** bloku znajdującego się w bloku **catch** . Następujący przykład jest nieprawidłowy:

[!code-cpp[NVC_MFCExceptions#12](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

Aby uzyskać więcej informacji, zobacz [wyjątki: Badanie zawartości wyjątku](exceptions-examining-exception-contents.md).

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków](exception-handling-in-mfc.md)
