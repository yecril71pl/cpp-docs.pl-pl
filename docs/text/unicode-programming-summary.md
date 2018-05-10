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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a378d46c517dfc0fbb5857ad54bc31f4c34287b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="unicode-programming-summary"></a>Podsumowanie programowania Unicode
Aby móc korzystać z obsługi czasu wykonywania MFC i C Unicode, musisz:  
  
-   Zdefiniuj **_unicode —**.  
  
     Zdefiniuj symbol **_unicode —** przed kompilacji programu.  
  
-   Określ punkt wejścia.  
  
     Na **dane wyjściowe** stronę folderu konsolidatora do projektu [strony właściwości](../ide/property-pages-visual-cpp.md) okna dialogowego należy ustawić symbol punktu wejścia **wWinMainCRTStartup**.  
  
-   Użycie przenośne funkcje wykonawcze języka i typów.  
  
     Użyj odpowiednie funkcje wykonawcze języka C do obsługi ciąg Unicode. Można użyć **wcs** rodziny funkcji, ale łączyli portable pełni (międzynarodowych włączone) **_tchar —** makra. Następujące makra są poprzedzane prefiksem **_tcs**; one podstawić, jeden dla jednego, dla **str** rodziny funkcji. Te funkcje są opisane szczegółowo w [internacjonalizacji](../c-runtime-library/internationalization.md) sekcji *odwołanie do biblioteki wykonawczej*. Aby uzyskać więcej informacji, zobacz [mapowania zwykłego tekstu w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
     Użyj **_tchar —** i pokrewne przenośne typy danych opisanego w [obsługę standardu Unicode](../text/support-for-unicode.md).  
  
-   Poprawnie obsłużyć ciągi literału.  
  
     Kompilator Visual C++ interpretuje literałem zakodowane jako:  
  
    ```  
    L"this is a literal string"  
    ```  
  
     oznacza to ciąg znaków Unicode. Można użyć tego samego prefiksu literał znaków. Użyj **_t —** makro kodu ciągi literału objęty, aby skompilować ich jako ciągów Unicode w obszarze Unicode lub ciągów ANSI (w tym MBCS) bez Unicode. Na przykład zamiast elementu:  
  
    ```  
    pWnd->SetWindowText( "Hello" );  
    ```  
  
     Za pomocą:  
  
    ```  
    pWnd->SetWindowText( _T("Hello") );  
    ```  
  
     Z **_unicode —** zdefiniowane, **_t —** tłumaczy literału ciągu do formularza prefiksem L; w przeciwnym razie **_t —** tłumaczy ciąg bez prefiksu L.  
  
    > [!TIP]
    >  **_T —** makro jest taki sam jak `_TEXT` makra.  
  
-   Należy zachować ostrożność podczas przekazywania długości ciągu do funkcji.  
  
     Niektóre funkcje mają liczba znaków w ciągu; inne osoby, która ma liczbę bajtów. Na przykład jeśli **_unicode —** jest zdefiniowany, następujące wywołanie do `CArchive` obiektu nie będzie działać (`str` jest `CString`):  
  
    ```  
    archive.Write( str, str.GetLength( ) );    // invalid  
    ```  
  
     W aplikacji Unicode długość daje liczba znaków, ale nie poprawną liczbę bajtów, ponieważ każdy znak jest 2 bajty szerokości. Zamiast tego należy użyć:  
  
    ```  
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid  
    ```  
  
     Określa, które poprawną liczbę bajtów do zapisania.  
  
     Jednak funkcje Członkowskie MFC, które są zorientowane na znak zamiast zorientowane na bajt działa bez to bardzo kodowanie:  
  
    ```  
    pDC->TextOut( str, str.GetLength( ) );  
    ```  
  
     `CDC::TextOut` pobiera liczbę znaków, nie liczba bajtów.  
  
-   Użyj [fopen_s —, _wfopen_s —](../c-runtime-library/reference/fopen-s-wfopen-s.md) do otwierania plików Unicode.  
  
 Podsumowując, MFC i biblioteki wykonawczej zapewniają obsługę programowania Unicode:  
  
-   Z wyjątkiem funkcji Członkowskich klasy bazy danych, wszystkie funkcje MFC obsługują Unicode, łącznie z `CString`. `CString` udostępnia funkcje konwersji Unicode/ANSI.  
  
-   Biblioteki wykonawczej udostępnia wszystkie funkcje obsługi ciągów Unicode wersji. (Biblioteki wykonawczej również udostępnia przenośnych odpowiedniej wersji Unicode lub MBCS. Są to **_tcs** makra.)  
  
-   Tchar.h dostarcza przenośne typy danych i **_t —** makro do tłumaczenia ciągi literału i znaki. Aby uzyskać więcej informacji, zobacz [mapowania zwykłego tekstu w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   Biblioteki wykonawczej dostarcza wersję znaków dwubajtowych **głównego**. Użyj **wmain** dokonanie aplikacji obsługujących Unicode.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa formatu Unicode](../text/support-for-unicode.md)