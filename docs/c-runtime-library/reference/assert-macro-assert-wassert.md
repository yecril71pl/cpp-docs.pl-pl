---
title: assert Macro, _assert, _wassert | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- assert
- _assert
- _wassert
apilocation:
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
apitype: DLLExport
f1_keywords:
- assert
- _assert
- _wassert
- assert/_wassert
dev_langs:
- C++
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c1d2bef607e80e2e972915bd8a8b0517b7c6e5eb
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43200670"
---
# <a name="assert-macro-assert-wassert"></a>assert Macro, _assert, _wassert

Oblicza wyrażenie i, jeśli wynik to **false**przerywa program i wyświetla komunikat diagnostyczny.

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

*wyrażenie* wyrażenie skalarne (w tym wyrażenia wskaźnika) obliczane na wartość różną od zera (**true**) lub równa 0 (**false**).

*komunikat* widomość do wyświetlenia.

*Nazwa pliku* nazwa źródła pliku asercja nie powiodła się.

*wiersz* liczbę wierszy w pliku źródłowym potwierdzenie nie powiodło się.

## <a name="remarks"></a>Uwagi

**Asercja** — makro jest zazwyczaj używany do identyfikowania błędów logicznych podczas tworzenia programu. Umożliwia zatrzymują wykonywanie programu w przypadku, gdy występują nieoczekiwane warunki, implementując *wyrażenie* argument na **false** tylko gdy program działa nieprawidłowo. Sprawdzanie potwierdzenia można wyłączyć w czasie kompilacji, definiując makro **NDEBUG**. Można wyłączyć **asercja** — makro bez konieczności modyfikacji plików źródłowych przy użyciu **/DNDEBUG** opcji wiersza polecenia. Można wyłączyć **asercja** makra w kodzie źródłowym za pomocą `#define NDEBUG` dyrektywy przed \<assert.h > jest dołączony.

**Asercja** drukuje makra diagnostyczne komunikatu podczas *wyrażenie* daje w wyniku **false** (0) i wywołuje [przerwać](abort.md) zakończyć program wykonanie. Jeśli zostanie podjęta żadna akcja *wyrażenie* jest **true** (niezerową). Komunikat diagnostyczny zawiera wyrażenie nie powiodło się, a Nazwa źródłowego pliku i numer wiersza gdzie potwierdzenie nie powiodło się.

Komunikat diagnostyczny jest drukowany w znaki dwubajtowe. W związku z tym będzie działać zgodnie z oczekiwaniami, nawet jeśli występują znaki Unicode w wyrażeniu.

Miejsce docelowe komunikat diagnostyczny zależy od typu aplikacji, która wywołana procedura. Aplikacje konsoli otrzymać komunikat za pośrednictwem **stderr**. W przypadku aplikacji z Windows **asercja** wywołuje Windows [MessageBox](/windows/desktop/api/winuser/nf-winuser-messagebox) funkcji, aby utworzyć okno komunikatu, aby wyświetlić wiadomość wraz z **OK** przycisku. Kiedy użytkownik kliknie **OK**, program przerywa natychmiast.

Gdy aplikacja jest połączona z wersji debugowania bibliotek wykonawczych **asercja** tworzy okno komunikatu o trzy przyciski: **przerwać**, **ponów próbę wykonania**i **Ignoruj**. Jeśli użytkownik kliknie **przerwać**, program przerywa natychmiast. Jeśli użytkownik kliknie **ponów**, wywoływana jest debugera i użytkownik mógł debugować program, jeśli włączone jest debugowanie just-in-time (JIT). Jeśli użytkownik kliknie **Ignoruj**, **asercja** kontynuuje normalne wykonywanie: tworzenie okno komunikatu z **OK** przycisku. Należy pamiętać, że kliknięcie **Ignoruj** gdy istnieje warunek błędu może spowodować niezdefiniowane zachowanie.

Aby uzyskać więcej informacji na temat debugowania CRT, zobacz [techniki testowania CRT](/visualstudio/debugger/crt-debugging-techniques).

**_Assert** i **_wassert** funkcje są wewnętrzne funkcje CRT. One pomóc zminimalizować kod wymagany w plikach obiektu do obsługi potwierdzenia. Firma Microsoft nie zaleca się bezpośrednio wywoływać tych funkcji.

**Asercja** — makro jest włączone w wersji wydania i debugowe wersji biblioteki wykonawczej C podczas **NDEBUG** nie został zdefiniowany. Gdy **NDEBUG** jest zdefiniowany, makro jest dostępna, ale jej argument nie może oszacować i nie ma wpływu. Po jej włączeniu **asercja** wywołania makra **_wassert** jego wdrażania. Inne makra potwierdzenie [_ASSERT](assert-asserte-assert-expr-macros.md), [_asserte —](assert-asserte-assert-expr-macros.md) i [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md), są również dostępne, ale tylko oceny wyrażenia przekazany do ich, kiedy [_DEBUG](../../c-runtime-library/debug.md) makro zostało zdefiniowane i, gdy są one w kodzie powiązanym z wersji debugowania bibliotek uruchomieniowych C.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**asercja**, **_wassert**|\<assert.h>|

Podpis **_assert** funkcja nie jest dostępna w pliku nagłówkowym. Podpis **_wassert** funkcja jest dostępna tylko podczas **NDEBUG** makro jest niezdefiniowane.

## <a name="example"></a>Przykład

W tym programie **analyze_string** używa funkcji **asercja** makra, aby przetestować kilka warunków związanych z ciągu i długości. Jeśli którykolwiek z warunków nie powiedzie się, program wyświetli komunikat wskazujący, co było przyczyną błędu.

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

Program generuje następujące dane wyjściowe:

```Output
Analyzing string 'abc'
Analyzing string '(null)'
Assertion failed: string != NULL, file crt_assert.c, line 25
```

Po niepowodzeniu potwierdzenie, w zależności od wersji systemu operacyjnego i biblioteki wykonawczej mogą pojawić się okno komunikatu, który zawiera podobny do poniższego:

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

Jeśli zainstalowany jest debugera, wybierz **debugowania** przycisk, aby uruchomić debuger, lub **Zamknij program** aby wyjść.

## <a name="see-also"></a>Zobacz także

[Obsługa błędów](../../c-runtime-library/error-handling-crt.md)<br/>
[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR Macros](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
