---
title: potwierdzj makro, _assert, _wassert
description: Efekty makr i funkcji potwierdzenia w środowisku uruchomieniowym języka C.
ms.date: 11/04/2016
api_name:
- assert
- _assert
- _wassert
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- assert
- _assert
- _wassert
- assert/_wassert
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
ms.openlocfilehash: 071424f2201ceda43438fe1056801811fe444a01
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609082"
---
# <a name="assert-macro-_assert-_wassert"></a>potwierdzj makro, _assert, _wassert

Oblicza wyrażenie i, gdy wynik jest **`false`** , drukuje komunikat diagnostyczny i przerywa program.

## <a name="syntax"></a>Składnia

```C
assert(
   expression
);
void _assert(
   char const* message,
   char const* filename,
   unsigned line
);
void _wassert(
   wchar_t const* message,
   wchar_t const* filename,
   unsigned line
);
```

### <a name="parameters"></a>Parametry

*wyrażenia*<br/>
Wyrażenie skalarne (w tym wyrażenia wskaźnika), które daje w wyniku wartość różną od zera ( **`true`** ) lub 0 ( **`false`** ).

*Komunikat*<br/>
Widomość do wyświetlenia.

*Nazwa pliku*<br/>
Nazwa pliku źródłowego, w którym potwierdzenie nie powiodło się.

*line*<br/>
Numer wiersza w pliku źródłowym potwierdzeń zakończonych niepowodzeniem.

## <a name="remarks"></a>Uwagi

`assert`Makro jest zwykle używane do identyfikowania błędów logiki podczas tworzenia programu. Służy do zatrzymywania wykonywania programu w przypadku nieoczekiwanych warunków przez implementację argumentu *Expression* do obliczenia **`false`** tylko wtedy, gdy program działa nieprawidłowo. Testy potwierdzenia można wyłączyć w czasie kompilacji, definiując **NDEBUG**makro. Można wyłączyć `assert` makro bez modyfikowania plików źródłowych przy użyciu opcji wiersza polecenia **/DNDEBUG** . Można wyłączyć `assert` makro w kodzie źródłowym przy użyciu `#define NDEBUG` dyrektywy, zanim \<assert.h> zostanie on uwzględniony.

`assert`Makro drukuje komunikat diagnostyczny, gdy *wyrażenie* zwróci wartość **`false`** (0) i wywołuje, [`abort`](abort.md) Aby zatrzymać wykonywanie programu. Nie jest podejmowana żadna akcja, jeśli *wyrażenie* jest **`true`** (niezerowe). Komunikat diagnostyczny zawiera niepowodzenie wyrażenie, nazwę pliku źródłowego i numer wiersza, w którym potwierdzenie nie powiodło się.

Komunikat diagnostyczny jest drukowany w postaci szerokiej litery ( `wchar_t` ). W związku z tym będzie działała zgodnie z oczekiwaniami, nawet jeśli w wyrażeniu znajdują się znaki Unicode.

Lokalizacja docelowa komunikatu diagnostycznego zależy od typu aplikacji, która wywołała procedurę. Aplikacje konsolowe odbierają komunikat za pomocą **stderr**. W aplikacji opartej na systemie Windows `assert` wywołuje funkcję [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) systemu Windows w celu utworzenia okna komunikatu, aby wyświetlić komunikat z trzema przyciskami: **Przerwij**, **Ponów**i **Ignoruj**. Jeśli użytkownik kliknie przycisk **Przerwij**, program natychmiast zostanie przerwany. Jeśli użytkownik kliknie przycisk **Ponów próbę**, debuger zostanie wywołany, a użytkownik będzie mógł debugować program, jeśli jest włączone debugowanie just-in-Time (JIT). Jeśli użytkownik kliknie przycisk **Ignoruj**, program będzie kontynuował normalne wykonywanie operacji. Kliknięcie przycisku **Ignoruj** , gdy istnieje warunek błędu, może spowodować niezdefiniowane zachowanie, ponieważ nie spełniono warunków wstępnych kodu wywołującego.

Aby zastąpić domyślne zachowanie danych wyjściowych niezależnie od typu aplikacji, należy wywołać [`_set_error_mode`](set-error-mode.md) wybór między zachowaniem danych wyjściowych do stderr i ekranem.

Po `assert` wyświetleniu komunikatu jest on wywoływany [`abort`](abort.md) , który wyświetla okno dialogowe z przyciskami  **Przerwij**, **Ponów**i **Ignoruj** . [`abort`](abort.md) zamyka program, dlatego przycisk **Ponów** i **zignoruj** nie wznawia wykonywania programu po `assert` wywołaniu. `assert`W przypadku wyświetlenia okna dialogowego okno [`abort`](abort.md) dialogowe nie jest wyświetlane. Jedyną chwilą [`abort`](abort.md) wyświetlania okna dialogowego jest `assert` wysyłanie danych wyjściowych do STDERR.

W związku z powyższym zachowaniem okno dialogowe jest zawsze wyświetlane po `assert` wywołaniu w trybie debugowania. Zachowanie każdego przycisku jest przechwytywane w poniższej tabeli.

|Tryb błędu|Dane wyjściowe do stderr (konsola/_OUT_TO_STDERR)|Okno dialogowe wyświetlania (Windows/_OUT_TO_MSGBOX)|
|----------|----------------|------------------|
|Przerwanie|Zakończ natychmiast z kodem zakończenia 3|Zakończ natychmiast z kodem zakończenia 3|
|Ponów próbę|Przerwij w debugerze podczas `abort`|Przerwij w debugerze podczas `assert`|
|Ignoruj|Zakończ zamykanie przez `abort`|Kontynuuj program tak, jakby potwierdzenie nie zostało wywołane (może spowodować niezdefiniowane zachowanie, ponieważ nie spełniono warunków wstępnych kodu wywołującego)|

Aby uzyskać więcej informacji na temat debugowania CRT, zobacz [techniki debugowania CRT](/visualstudio/debugger/crt-debugging-techniques).

`_assert`Funkcje i `_wassert` są wewnętrznymi funkcjami CRT. Pomagają zminimalizować kod wymagany w plikach obiektów do obsługi potwierdzeń. Nie zalecamy bezpośredniego wywoływania tych funkcji.

`assert`Makro jest włączane zarówno w wersji wersji, jak i w debugowaniu bibliotek uruchomieniowych C, gdy **NDEBUG** nie jest zdefiniowany. Gdy **NDEBUG** jest zdefiniowany, makro jest dostępne, ale nie oblicza jego argumentu i nie ma wpływu. Gdy jest włączona, `assert` makro wywołuje `_wassert` do jego implementacji. Dostępne są również inne makra potwierdzania, [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md) i [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md), ale tylko są oceniane tylko wyrażenia przesłane do nich, gdy makro [_DEBUG](../../c-runtime-library/debug.md) zostało zdefiniowane i gdy znajdują się w kodzie połączonym z wersją debugową bibliotek uruchomieniowych C.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|`assert`, `_wassert`|\<assert.h>|

Podpis `_assert` funkcji nie jest dostępny w pliku nagłówkowym. Podpis `_wassert` funkcji jest dostępny tylko wtedy, gdy makro **NDEBUG** nie jest zdefiniowane.

## <a name="example"></a>Przykład

W tym programie funkcja **analyze_string** używa `assert` makra do testowania kilku warunków związanych z ciągiem i długością. Jeśli którykolwiek z warunków zakończy się niepowodzeniem, program drukuje komunikat informujący o tym, co spowodowało błąd.

```C
// crt_assert.c
// compile by using: cl /W4 crt_assert.c
#include <stdio.h>
#include <assert.h>
#include <string.h>

void analyze_string( char *string );   // Prototype

int main( void )
{
   char  test1[] = "abc", *test2 = NULL, test3[] = "";

   printf ( "Analyzing string '%s'\n", test1 ); fflush( stdout );
   analyze_string( test1 );
   printf ( "Analyzing string '%s'\n", test2 ); fflush( stdout );
   analyze_string( test2 );
   printf ( "Analyzing string '%s'\n", test3 ); fflush( stdout );
   analyze_string( test3 );
}

// Tests a string to see if it is NULL,
// empty, or longer than 0 characters.
void analyze_string( char * string )
{
   assert( string != NULL );        // Cannot be NULL
   assert( *string != '\0' );       // Cannot be empty
   assert( strlen( string ) > 2 );  // Length must exceed 2
}
```

Program generuje te dane wyjściowe:

```Output
Analyzing string 'abc'
Analyzing string '(null)'
Assertion failed: string != NULL, file crt_assert.c, line 25
```

Po błędzie potwierdzenia, w zależności od wersji systemu operacyjnego i biblioteki wykonawczej, może pojawić się okno komunikatu zawierające coś podobnego do:

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

Jeśli jest zainstalowany debuger, wybierz przycisk **Debuguj** , aby uruchomić debuger, lub **Zamknij program** , aby wyjść.

## <a name="see-also"></a>Zobacz też

[Obsługa błędów](../../c-runtime-library/error-handling-crt.md)<br/>
[Proces i kontrola środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[Anuluj](abort.md)<br/>
[nosić](raise.md)<br/>
[sygnał](signal.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR makra](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
