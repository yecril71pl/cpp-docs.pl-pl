---
title: Podsumowanie programowania Unicode
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
ms.openlocfilehash: 5095e1c58db3e5c35eb9215367f2fbb064bc228a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504703"
---
# <a name="unicode-programming-summary"></a>Podsumowanie programowania Unicode

Aby skorzystać z obsługi MFC i języka C w czasie wykonywania dla standardu Unicode, należy wykonać następujące działania:

- Zdefiniuj `_UNICODE` .

   Zdefiniuj symbol `_UNICODE` przed kompilacją programu.

- Określ punkt wejścia.

   Na stronie **Zaawansowane** folderu **konsolidatora** w oknie dialogowym [strony właściwości](../build/reference/property-pages-visual-cpp.md) projektu Ustaw symbol **punktu wejścia** `wWinMainCRTStartup` .

- Używaj przenośnych funkcji i typów w czasie wykonywania.

   Użyj odpowiednich funkcji języka C do obsługi ciągów Unicode. Możesz użyć `wcs` rodziny funkcji, ale możesz preferować w pełni przenośne (z ograniczeniami) `_TCHAR` . Wszystkie te makra są poprzedzone prefiksem `_tcs` , po jednym dla jednej z nich, na potrzeby `str` rodziny funkcji. Te funkcje są szczegółowo opisane [w sekcji Informacje ogólne w](../c-runtime-library/internationalization.md) *dokumentacji dotyczącej biblioteki wykonawczej*. Aby uzyskać więcej informacji, zobacz [Mapowanie tekstu ogólnego w używanie TCHAR. h](../text/generic-text-mappings-in-tchar-h.md).

   Używaj `_TCHAR` i powiązanych przenośnych typów danych opisanych w temacie [Obsługa standardu Unicode](../text/support-for-unicode.md).

- Prawidłowo Obsługuj ciągi literału.

   Kompilator Visual C++ interpretuje ciąg literału zakodowany jako:

    ```cpp
    L"this is a literal string"
    ```

   do oznaczania ciągu znaków Unicode. Można użyć tego samego prefiksu dla znaków literału. Używaj `_T` makra do kodu literału w sposób ogólny, dlatego kompilują jako ciągi Unicode w formacie Unicode lub jako ciągi ANSI (w tym MBCS) bez kodu Unicode. Na przykład zamiast:

    ```cpp
    pWnd->SetWindowText( "Hello" );
    ```

   używanych

    ```cpp
    pWnd->SetWindowText( _T("Hello") );
    ```

   Ze `_UNICODE` zdefiniowaną funkcją `_T` tłumaczy ciąg literału na formularz z prefiksem l. w przeciwnym razie program `_T` tłumaczy ciąg bez prefiksu l.

    > [!TIP]
    >  `_T`Makro jest identyczne z `_TEXT` makrem.

- Należy zachować ostrożność przekazywania długości ciągu do funkcji.

   Niektóre funkcje mają liczbę znaków w ciągu; inne osoby chcą mieć liczbę bajtów. Na przykład, jeśli `_UNICODE` jest zdefiniowany, następujące wywołanie do `CArchive` obiektu nie będzie działało ( `str` is `CString` ):

    ```cpp
    archive.Write( str, str.GetLength( ) );    // invalid
    ```

   W aplikacji Unicode długość zawiera liczbę znaków, ale nie liczbę bajtów, ponieważ każdy znak ma szerokość 2 bajtów. Zamiast tego należy użyć:

    ```cpp
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid
    ```

   Określa poprawną liczbę bajtów do zapisania.

   Jednak funkcje elementów członkowskich MFC, które są zorientowane znakowo, a nie zorientowane na bajty, działają bez tego dodatkowego kodowania:

    ```cpp
    pDC->TextOut( str, str.GetLength( ) );
    ```

   `CDC::TextOut` przyjmuje liczbę znaków, nie liczbę bajtów.

- Użyj [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) do otwierania plików Unicode.

Aby podsumować, MFC i Biblioteka wykonawcza zapewniały następujące wsparcie dla programowania Unicode:

- Z wyjątkiem funkcji składowych klasy bazy danych, wszystkie funkcje MFC są włączone w formacie Unicode, w tym `CString` . `CString` udostępnia również funkcje konwersji Unicode/ANSI.

- Biblioteka wykonawcza dostarcza wersje Unicode wszystkich funkcji obsługi ciągów. (Biblioteka wykonawcza udostępnia również przenośne wersje odpowiednie dla standardu Unicode lub MBCS. Są to `_tcs` makra.)

- Używanie TCHAR. h dostarcza przenośne typy danych i `_T` makro do tłumaczenia ciągów literałów i znaków. Aby uzyskać więcej informacji, zobacz [Mapowanie tekstu ogólnego w używanie TCHAR. h](../text/generic-text-mappings-in-tchar-h.md).

- Biblioteka wykonawcza zapewnia wersję o szerokim znaku `main` . Użyj `wmain` , aby udostępnić aplikację Unicode.

## <a name="see-also"></a>Zobacz też

[Obsługa formatu Unicode](../text/support-for-unicode.md)
