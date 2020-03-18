---
title: Operacje We/Wy konsoli i portu
ms.date: 11/04/2016
helpviewer_keywords:
- routines, console and port I/O
- routines
- ports, I/O routines
- I/O [CRT], console
- I/O [CRT], port
- I/O routines, console and port I/O
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
ms.openlocfilehash: 5b4dc2a081ea11bd84d932f55b5b247de81f296a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443448"
---
# <a name="console-and-port-io"></a>Operacje We/Wy konsoli i portu

Te procedury służą do odczytu i zapisu w konsoli lub na określonym porcie. Procedury we/wy konsoli nie są zgodne z procedurami operacji we/wy strumienia i/O niskim poziomie. Przed wykonaniem operacji we/wy nie trzeba otwierać ani zamykać konsoli lub portu. w tej kategorii nie ma żadnych otwartych ani zamykających procedur. W systemach operacyjnych Windows dane wyjściowe z tych funkcji są zawsze kierowane do konsoli i nie można ich przekierować.

## <a name="console-and-port-io-routines"></a>Procedury we/wy konsoli i portu

|Procedura|Użycie|
|-------------|---------|
|[_cgets, _cgetws](../c-runtime-library/cgets-cgetws.md), [_cgets_s _cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|Odczytaj ciąg z konsoli|
|[_cprintf, _cwprintf](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md), [_cprintf_s, _cprintf_s_l, _cwprintf_s](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md) _cwprintf_s_l|Zapisz sformatowane dane w konsoli|
|[_cputs](../c-runtime-library/reference/cputs-cputws.md)|Napisz ciąg do konsoli|
|[_cscanf, _cwscanf](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md), [_cscanf_s, _cscanf_s_l, _cwscanf_s](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md) _cwscanf_s_l|Odczytaj sformatowane dane z konsoli|
|[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)|Odczytaj znak z konsoli|
|[_getche, _getwche](../c-runtime-library/reference/getch-getwch.md)|Odczytaj znak z konsoli i echo go|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|Odczytaj jeden bajt z określonego portu we/wy|
|[_inpd](../c-runtime-library/inp-inpw-inpd.md)|Przeczytaj podwójne słowo z określonego portu we/wy|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|Przeczytaj 2-bajtowy wyraz z określonego portu we/wy|
|[_kbhit](../c-runtime-library/reference/kbhit.md)|Sprawdź naciśnięcie klawisza w konsoli programu; Użyj przed podjęciem próby odczytu z konsoli|
|[_outp](../c-runtime-library/outp-outpw-outpd.md)|Napisz jeden bajt do określonego portu we/wy|
|[_outpd](../c-runtime-library/outp-outpw-outpd.md)|Napisz podwójny wyraz do określonego portu we/wy|
|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|Napisz wyraz do określonego portu we/wy|
|[_putch, _putwch](../c-runtime-library/reference/putch-putwch.md)|Napisz znak do konsoli|
|[_ungetch, _ungetwch](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|"Unget" ostatni znak odczytywany z konsoli, tak aby stał się następnym znakiem odczytu|

## <a name="see-also"></a>Zobacz też

[Dane wejściowe i wyjściowe](../c-runtime-library/input-and-output.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
