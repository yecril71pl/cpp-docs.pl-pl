---
title: Podsumowanie programowania Unicode | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d49f87d5709483a36325afa426a790374fc93837
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415814"
---
# <a name="unicode-programming-summary"></a>Podsumowanie programowania Unicode

Aby móc korzystać z pomocy technicznej czasu wykonywania MFC i C obsługi standardu Unicode, należy:

- Zdefiniuj `_UNICODE`.

   Zdefiniuj symbol `_UNICODE` przed dokonaniem kompilacji programu.

- Określ punkt wejścia.

   Na **dane wyjściowe** strony **konsolidatora** folderu w projekcie [stron właściwości](../ide/property-pages-visual-cpp.md) okno dialogowe, zestaw **punktu wejścia** symbol `wWinMainCRTStartup`.

- Użyj przenośne funkcji wykonawczej i typów.

   Odpowiednie funkcje języka C w czasie wykonywania na użytek obsługi ciąg Unicode. Możesz użyć `wcs` rodzinę funkcji, możesz preferować przenośna pełni (w wielu krajach włączone) `_TCHAR` makra. Te makra są poprzedzone z `_tcs`; mogą zastąpić, jeden do jednego, dla `str` rodziny funkcji. Te funkcje są szczegółowo opisane w [internacjonalizacji](../c-runtime-library/internationalization.md) części *odwołanie do biblioteki wykonawczej*. Aby uzyskać więcej informacji, zobacz [mapowania typ ogólny-tekst w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md).

   Użyj `_TCHAR` i powiązane przenośne typy danych opisanych w [Obsługa formatu Unicode](../text/support-for-unicode.md).

- Poprawnie obsługiwać ciągi literałowe.

   Kompilator języka Visual C++ interpretuje ciąg literału zakodowane jako:

    ```cpp
    L"this is a literal string"
    ```

   oznacza to ciąg znaków Unicode. Można użyć tego samego prefiksu dla znaki literału. Użyj `_T` makra o kodowaniu ciągi literałowe ogólną, aby skompilować ich jako ciągi Unicode w Unicode lub ciągów ANSI (w tym MBCS) bez Unicode. Na przykład zamiast programu:

    ```cpp
    pWnd->SetWindowText( "Hello" );
    ```

   Użycie:

    ```cpp
    pWnd->SetWindowText( _T("Hello") );
    ```

   Za pomocą `_UNICODE` zdefiniowane, `_T` tłumaczy ciągiem literału formularza poprzedzone L; w przeciwnym razie `_T` tłumaczy ciąg bez przedrostka L.

    > [!TIP]
    >  `_T` — Makro jest taka sama jak `_TEXT` makra.

- Należy zachować ostrożność przekazywania długości ciągów do funkcji.

   Niektóre funkcje mają liczbę znaków w ciągu; inne osoby mają liczbę bajtów. Na przykład jeśli `_UNICODE` jest zdefiniowany, wywołanie następujące `CArchive` obiekt nie będzie działać (`str` jest `CString`):

    ```cpp
    archive.Write( str, str.GetLength( ) );    // invalid
    ```

   W aplikacji Unicode długość daje liczbę znaków, ale nie poprawną liczbę bajtów, ponieważ każdy znak jest szeroki 2 bajty. Zamiast tego należy użyć:

    ```cpp
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid
    ```

   który określa poprawną liczbę bajtów do zapisania.

   Jednak funkcje Członkowskie MFC, które są zorientowane na znak, a nie zorientowane na bajt działać bez to bardzo kodowania:

    ```cpp
    pDC->TextOut( str, str.GetLength( ) );
    ```

     `CDC::TextOut` pobiera liczbę znaków, nie liczbę bajtów.

- Użyj [fopen_s —, _wfopen_s —](../c-runtime-library/reference/fopen-s-wfopen-s.md) do otwierania plików Unicode.

Aby podsumować, MFC i biblioteki wykonawczej zapewniają obsługę programowania Unicode:

- Z wyjątkiem funkcji składowych klasy bazy danych, wszystkie funkcje MFC obsługują Unicode, w tym `CString`. `CString` udostępnia również funkcje konwersji Unicode/ANSI.

- Biblioteka środowiska uruchomieniowego dostarcza wersje wszystkich funkcji obsługi ciągów Unicode. (Biblioteki wykonawczej dostarcza również wersje przenośnym odpowiednie dla Unicode lub MBCS. Są to `_tcs` makra.)

- Tchar.h dostarcza przenośne typy danych i `_T` makra do tłumaczenia ciągów literałów i znaków. Aby uzyskać więcej informacji, zobacz [mapowania typ ogólny-tekst w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md).

- Biblioteka środowiska uruchomieniowego zawiera wersja znaków dwubajtowych `main`. Użyj `wmain` aplikacji obsługujących Unicode.

## <a name="see-also"></a>Zobacz też

[Obsługa formatu Unicode](../text/support-for-unicode.md)