---
title: Operacje We/Wy konsoli i portu
ms.date: 11/04/2016
f1_keywords:
- c.io
helpviewer_keywords:
- routines, console and port I/O
- routines
- ports, I/O routines
- I/O [CRT], console
- I/O [CRT], port
- I/O routines, console and port I/O
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
ms.openlocfilehash: 728ff6fa36d21e869c65db705b25bbe7c9d711ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446764"
---
# <a name="console-and-port-io"></a>Operacje We/Wy konsoli i portu

Te procedury i zapis na konsoli lub na określonym porcie. Procedury we/wy konsoli nie są zgodne z we/wy strumienia lub procedury we/wy niskiego poziomu w bibliotece. Konsoli lub portu nie musi być otwarte lub zamknięte przed wykonaniem operacji We/Wy, więc istnieją nie otwierania lub zamykania procedury w tej kategorii. W systemach operacyjnych Windows dane wyjściowe z tych funkcji są zawsze kierowane do konsoli i nie można przekierować.

## <a name="console-and-port-io-routines"></a>Procedury we/wy konsoli i portu

|Procedura|Zastosowanie|
|-------------|---------|
|[_cgets, _cgetws —](../c-runtime-library/cgets-cgetws.md), [_cgets_s, _cgetws_s —](../c-runtime-library/reference/cgets-s-cgetws-s.md)|Parametry odczytu z konsoli|
|[_cprintf, _cwprintf —](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md), [_cprintf_s, _cprintf_s_l —, _cwprintf_s —, _cwprintf_s_l —](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|Wpisz sformatowane dane do konsoli|
|[_cputs —](../c-runtime-library/reference/cputs-cputws.md)|Zapisz ciąg do konsoli|
|[_cscanf, _cwscanf —](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md), [_cscanf_s —, _cscanf_s_l —, _cwscanf_s —, _cwscanf_s_l —](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|Odczyt sformatowanych danych z poziomu konsoli|
|[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)|Przeczytaj znak z konsoli|
|[_getche, _getwche](../c-runtime-library/reference/getch-getwch.md)|Odczytywanie znaków z konsoli i echo go|
|[_inp —](../c-runtime-library/inp-inpw-inpd.md)|Odczyt jednobajtowego z określonego portu We/Wy|
|[_inpd —](../c-runtime-library/inp-inpw-inpd.md)|Odczyt podwójne słowo z określonego portu We/Wy|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|Odczyt word 2-bajtowych z określonego portu We/Wy|
|[_kbhit](../c-runtime-library/reference/kbhit.md)|Sprawdź, czy naciśnięcia klawisza konsoli; Użycie przed podjęciem próby wykonania do odczytywania z konsoli|
|[_outp —](../c-runtime-library/outp-outpw-outpd.md)|Zapis jednobajtowego do określonego portu We/Wy|
|[_outpd —](../c-runtime-library/outp-outpw-outpd.md)|Zapis podwójne słowo do określonego portu We/Wy|
|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|Pisanie programu word do określonego portu We/Wy|
|[_putch, _putwch](../c-runtime-library/reference/putch-putwch.md)|Wpisz znak do konsoli|
|[_ungetch, _ungetwch —](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|"Unget —" odczytu z poziomu konsoli, staje się ona następnym znakiem odczytanym ostatni znak|

## <a name="see-also"></a>Zobacz też

[Dane wejściowe i wyjściowe](../c-runtime-library/input-and-output.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>