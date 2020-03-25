---
title: Potwierdzanie i komunikaty dostarczone przez użytkownika (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- user-supplied messages [C++], run time
- user-supplied messages [C++], preprocessor time
- '#error%2C assert%2C static_assert [C++]'
- user-supplied messages [C++], compile time
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
ms.openlocfilehash: d76f0c2f7dc5a4202bff3f93e097a1c186f4601a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190563"
---
# <a name="assertion-and-user-supplied-messages-c"></a>Potwierdzanie i komunikaty dostarczone przez użytkownika (C++)

C++ Język obsługuje trzy mechanizmy obsługi błędów, które ułatwiają debugowanie aplikacji: [dyrektywa #error](../preprocessor/hash-error-directive-c-cpp.md), słowo kluczowe [static_assert](../cpp/static-assert.md) i [makro Assert, _ASSERT, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) makro. Wszystkie trzy mechanizmy emitują komunikaty o błędach a dwa testują również potwierdzenia oprogramowania. Potwierdzenie oprogramowania określa warunek, który powinien być prawdziwy w konkretnym punkcie w programie. Jeśli potwierdzenia w czasie kompilacji zakończą się niepowodzeniem, kompilator generuje komunikat diagnostyczny i błąd kompilacji. Jeśli potwierdzenia czasu wykonania nie powiodą się, system operacyjny wysyła komunikat diagnostyczny i zamyka aplikację.

## <a name="remarks"></a>Uwagi

Okres istnienia aplikacji składa się z fazy przetwarzania wstępnego, fazy kompilacji i fazy czasu wykonywania. Każdy mechanizm obsługi błędów uzyskuje dostęp do informacji debugowania, które są dostępne podczas jednej z tych faz. Aby debugować skutecznie, wybierz ten mechanizm, który zapewnia odpowiednie informacje na temat tej fazy:

- [Dyrektywa #error](../preprocessor/hash-error-directive-c-cpp.md) obowiązuje podczas przetwarzania wstępnego. Bezwarunkowo emituje komunikat określony przez użytkownika i powoduje niepowodzenie wskutek błędu kompilacji. Wiadomość może zawierać tekst, który jest przetwarzany przez dyrektywy preprocesora, ale żadne wyrażenie warunkowe nie zostaje ocenione.

- Deklaracja [static_assert](../cpp/static-assert.md) obowiązuje w czasie kompilacji. Sprawdza potwierdzenia oprogramowania, które są reprezentowane przez wyrażenia integralne określone przez użytkownika, które można przekonwertować na wartość logiczną. Jeśli wyrażenie ma wartość zero (false), kompilator generuje komunikat określony przez użytkownika i kompilacja nie powiedzie się z powodu błędu.

   Deklaracja `static_assert` jest szczególnie przydatna podczas debugowania szablonów, ponieważ argumenty szablonu mogą być zawarte w wyrażeniu określonym przez użytkownika.

- [Makro Assert, _ASSERT, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) makro jest stosowane w czasie wykonywania. Ocenia wyrażenia określone przez użytkownika, a jeśli wynik wynosi zero, system wysyła komunikat diagnostyczny i zamyka aplikację. Wiele innych makr, takich jak[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) i _ASSERTE, przypomina to makro, ale wystawia inne komunikaty diagnostyczne zdefiniowane przez system lub zdefiniowane przez użytkownika.

## <a name="see-also"></a>Zobacz też

[#error, dyrektywa (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)<br/>
[assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR Macros](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)<br/>
[static_assert](../cpp/static-assert.md)<br/>
[_STATIC_ASSERT Macro](../c-runtime-library/reference/static-assert-macro.md)<br/>
[Szablony](../cpp/templates-cpp.md)
