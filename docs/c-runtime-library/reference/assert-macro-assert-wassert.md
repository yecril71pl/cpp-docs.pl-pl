---
title: potwierdzj makro, _assert, _wassert
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
ms.openlocfilehash: 173974cfd9d3f9b3fc054bb71ad70b757f8ef819
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232628"
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

*liniow*<br/>
Numer wiersza w pliku źródłowym potwierdzeń zakończonych niepowodzeniem.

## <a name="remarks"></a>Uwagi

Makro **Assert** jest zwykle używane do identyfikowania błędów logiki podczas tworzenia programu. Służy do zatrzymywania wykonywania programu w przypadku nieoczekiwanych warunków przez implementację argumentu *Expression* do obliczenia **`false`** tylko wtedy, gdy program działa nieprawidłowo. Testy potwierdzenia można wyłączyć w czasie kompilacji, definiując **NDEBUG**makro. Można wyłączyć makro **Assert** bez modyfikowania plików źródłowych przy użyciu opcji wiersza polecenia **/DNDEBUG** . Można wyłączyć makro **Assert** w kodzie źródłowym przy użyciu `#define NDEBUG` dyrektywy przed \<assert.h> dołączonym.

Makro **potwierdzenia** drukuje komunikat diagnostyczny, gdy *wyrażenie* zwróci wartość **`false`** (0), a wywołania [przerywają](abort.md) działanie, aby przerwać wykonywanie programu. Nie jest podejmowana żadna akcja, jeśli *wyrażenie* jest **`true`** (niezerowe). Komunikat diagnostyczny zawiera niepowodzenie wyrażenie, nazwę pliku źródłowego i numer wiersza, w którym potwierdzenie nie powiodło się.

Komunikat diagnostyczny jest drukowany w postaci dwubajtowej. W ten sposób będzie działał zgodnie z oczekiwaniami, nawet jeśli w wyrażeniu znajdują się znaki Unicode.

Lokalizacja docelowa komunikatu diagnostycznego zależy od typu aplikacji, która wywołała procedurę. Aplikacje konsolowe zawsze odbierają komunikat przy użyciu **stderr**. W aplikacji opartej na systemie Windows, **Assert** wywołuje funkcję [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) systemu Windows w celu utworzenia okna komunikatu, aby wyświetlić komunikat i przycisk **OK** . Gdy użytkownik kliknie **przycisk OK**, program natychmiast przerywa działanie.

Gdy aplikacja jest połączona z wersją debugową bibliotek czasu wykonywania, **Assert** tworzy okno komunikatu z trzema przyciskami: **Przerwij**, **Ponów**i **Ignoruj**. Jeśli użytkownik kliknie przycisk **Przerwij**, program natychmiast zostanie przerwany. Jeśli użytkownik kliknie przycisk **Ponów próbę**, debuger zostanie wywołany, a użytkownik będzie mógł debugować program, jeśli jest włączone debugowanie just-in-Time (JIT). Jeśli użytkownik kliknie przycisk **Ignoruj**, **potwierdzenie** będzie kontynuowane w normalnym wykonaniu: Tworzenie okna komunikatu z przyciskiem **OK** . Należy pamiętać, że kliknięcie przycisku **Ignoruj** , gdy istnieje warunek błędu może spowodować niezdefiniowane zachowanie.

Aby uzyskać więcej informacji na temat debugowania CRT, zobacz [techniki debugowania CRT](/visualstudio/debugger/crt-debugging-techniques).

Funkcje **_ASSERT** i **_wassert** są wewnętrznymi funkcjami CRT. Pomagają zminimalizować kod wymagany w plikach obiektów do obsługi potwierdzeń. Nie zalecamy bezpośredniego wywoływania tych funkcji.

Makro **Assert** jest włączane w wersjach wersji i debugowania bibliotek uruchomieniowych C, gdy **NDEBUG** nie jest zdefiniowany. Gdy **NDEBUG** jest zdefiniowany, makro jest dostępne, ale nie oblicza jego argumentu i nie ma wpływu. Gdy ta funkcja jest włączona, makro **potwierdzenia** wywołuje **_wassert** do jego implementacji. Dostępne są również inne makra potwierdzania, [_ASSERT](assert-asserte-assert-expr-macros.md), [_ASSERTE](assert-asserte-assert-expr-macros.md) i [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md), ale tylko są oceniane tylko wyrażenia przesłane do nich, gdy makro [_DEBUG](../../c-runtime-library/debug.md) zostało zdefiniowane i gdy znajdują się w kodzie połączonym z wersją debugową bibliotek uruchomieniowych C.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Assert**, **_wassert**|\<assert.h>|

Podpis funkcji **_ASSERT** nie jest dostępny w pliku nagłówkowym. Sygnatura funkcji **_wassert** jest dostępna tylko wtedy, gdy makro **NDEBUG** nie jest zdefiniowane.

## <a name="example"></a>Przykład

W tym programie funkcja **analyze_string** używa makra **Assert** do testowania kilku warunków związanych z ciągiem i długością. Jeśli którykolwiek z warunków zakończy się niepowodzeniem, program drukuje komunikat informujący o tym, co spowodowało błąd.

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

Po błędzie potwierdzenia, w zależności od wersji systemu operacyjnego i biblioteki wykonawczej, może pojawić się okno komunikatu, które zawiera podobne:

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

Jeśli jest zainstalowany debuger, wybierz przycisk **Debuguj** , aby uruchomić debuger, lub **Zamknij program** , aby wyjść.

## <a name="see-also"></a>Zobacz także

[Obsługa błędów](../../c-runtime-library/error-handling-crt.md)<br/>
[Proces i kontrola środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[przerwij](abort.md)<br/>
[wywołaj](raise.md)<br/>
[sygnał](signal.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR makra](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
