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
ms.openlocfilehash: 0318abde877e9b647c1781408d2e22cc9d70824e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397844"
---
# <a name="assert-macro-assert-wassert"></a>assert Macro, _assert, _wassert

Oblicza wyrażenie i, gdy wynik jest **false**, drukuje wiadomość diagnostycznych i przerywa ten program.

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

*wyrażenie* wyrażenie skalarne (w tym wyrażenia wskaźnika) obliczane na niezerową (**true**) lub równa 0 (**false**).

*komunikat* komunikat do wyświetlenia.

*Nazwa pliku* potwierdzenia nie powiodło się w pliku nazwę źródła.

*wiersz* numer wiersza w pliku źródłowym potwierdzenia nie powiodło się.

## <a name="remarks"></a>Uwagi

**Assert** makro jest zwykle używane do identyfikowania logiki błędy podczas tworzenia programu. Należy zatrzymać wykonania programu, gdy występują nieoczekiwane warunki zaimplementowanie *wyrażenie* argument mogła zwrócić **false** tylko jeśli program działa nieprawidłowo. Sprawdzanie potwierdzenia można wyłączyć w czasie kompilacji poprzez definiowanie makro **NDEBUG**. Można wyłączyć **assert** makro bez konieczności modyfikacji plików źródłowych przy użyciu **/DNDEBUG** opcji wiersza polecenia. Można wyłączyć **assert** makra w kodzie źródłowym przy użyciu `#define NDEBUG` dyrektywy przed \<assert.h > jest dołączony.

**Assert** odbitek makra diagnostyczne komunikatu podczas obliczania *wyrażenie* daje w wyniku **false** (0) i wywołania [przerwać](abort.md) zakończenie programu wykonanie. Nie podjęto żadnej akcji Jeśli *wyrażenie* jest **true** (różną od zera). Diagnostycznych komunikat zawiera wyrażenie nie powiodło się, nazwy plików i wierszy numer źródłowego których potwierdzenia nie powiodło się.

Komunikat diagnostyczne jest drukowany w znaki dwubajtowe. W związku z tym będzie działać zgodnie z oczekiwaniami, nawet jeśli istnieją znaki Unicode w wyrażeniu.

Miejsce docelowe diagnostycznych wiadomości zależy od typu aplikacji, który wywołał procedurę. Aplikacje konsoli zawsze komunikatu za pośrednictwem **stderr**. W aplikacji systemu Windows **assert** wymaga systemu Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) funkcji, aby utworzyć komunikat, aby wyświetlić komunikat wraz z programem **OK** przycisku. Po kliknięciu przez użytkownika **OK**, program przerywa natychmiast.

Gdy aplikacja jest połączony z wersją biblioteki wykonawcze debugowania **assert** tworzy okno komunikatu o trzy przyciski: **przerwać**, **ponów**i **Ignoruj**. Gdy użytkownik kliknie **przerwać**, program przerywa natychmiast. Gdy użytkownik kliknie **ponów**, jest nazywany debugera i użytkownika można zdebugować program, jeśli włączone jest debugowanie just-in-time (JIT). Gdy użytkownik kliknie **Ignoruj**, **assert** będzie kontynuowane przy użyciu normalnego działania: Tworzenie pola wiadomości z **OK** przycisku. Należy pamiętać, że kliknięcie pozycji **Ignoruj** gdy istnieje warunek błędu może spowodować niezdefiniowane zachowanie.

Aby uzyskać więcej informacji na temat debugowania CRT, zobacz [techniki testowania CRT](/visualstudio/debugger/crt-debugging-techniques).

**_Assert** i **_wassert** funkcje są funkcje CRT wewnętrznej. One zminimalizować kod wymagany w plikach obiektu do obsługi potwierdzenia. Nie zaleca się bezpośrednio wywoływać te funkcje.

**Assert** makro jest włączone w wersji i debugowania wersji biblioteki wykonawcze języka C podczas **NDEBUG** nie jest zdefiniowany. Gdy **NDEBUG** jest zdefiniowany, makro jest dostępny, ale nie może oszacować jej argument i nie ma wpływu. Gdy jest włączone, **assert** wywołania makro **_wassert** jego wdrażania. Inne makra potwierdzenia [_ASSERT](assert-asserte-assert-expr-macros.md), [_asserte —](assert-asserte-assert-expr-macros.md) i [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md), są również dostępne, ale tylko ocenić wyrażenia przekazanych do nich, kiedy [_DEBUG](../../c-runtime-library/debug.md) makro zostało zdefiniowane i, gdy są połączone z wersją biblioteki wykonawcze języka C debugowania kodu.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|
|-------------|---------------------|
|**Assert**, **_wassert**|\<assert.h>|

Podpis **_assert** funkcja nie jest dostępna w pliku nagłówka. Podpis **_wassert** funkcja jest dostępna tylko podczas **NDEBUG** makro nie jest zdefiniowany.

## <a name="example"></a>Przykład

W tym programie **analyze_string** używa **assert** makro do testowania kilka warunków związanych z ciągu i długości. Jeśli jeden z warunków nie powiedzie się, program wyświetla komunikat informujący o przyczynach błędu.

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

Po błędzie potwierdzenia, w zależności od wersji systemu operacyjnego i biblioteki wykonawczej może zostać wyświetlony komunikat, który zawiera postać zbliżoną do następującej:

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

Jeśli debugera jest zainstalowana, wybierz **debugowania** przycisk, aby uruchomić debugera, lub **Zamknij program** aby zakończyć.

## <a name="see-also"></a>Zobacz także

[Obsługa błędów](../../c-runtime-library/error-handling-crt.md)<br/>
[Procedury kontroli środowiska](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT, _ASSERTE, _ASSERT_EXPR Macros](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
