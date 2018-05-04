---
title: We/Wy konsoli i portu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- routines, console and port I/O
- routines
- ports, I/O routines
- I/O [CRT], console
- I/O [CRT], port
- I/O routines, console and port I/O
ms.assetid: 0eee1c92-9b3d-41e0-a43a-257e546eeec8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e4d46582266234b4208a768fc7b2045af824349
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="console-and-port-io"></a>Operacje We/Wy konsoli i portu

Te procedury odczytu i zapisu w konsoli lub na określonym porcie. Procedury we/wy konsoli nie są zgodne z we/wy strumienia lub procedury biblioteki we/wy niskiego poziomu. Konsoli lub portu nie musi być otwarty lub zamknięty przed wykonaniem operacji We/Wy, więc nie bez otwierania lub zamykania procedury w tej kategorii. W systemach operacyjnych Windows dane wyjściowe z tych funkcji zawsze są kierowane do konsoli i nie może zostać przekierowane.

## <a name="console-and-port-io-routines"></a>Procedury we/wy konsoli i portu

|Procedura|Zastosowanie|
|-------------|---------|
|[_cgets —, _cgetws —](../c-runtime-library/cgets-cgetws.md), [_cgets_s —, _cgetws_s —](../c-runtime-library/reference/cgets-s-cgetws-s.md)|Parametry odczytu z konsoli|
|[_cprintf —, _cwprintf —](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md), [_cprintf_s —, _cprintf_s_l —, _cwprintf_s —, _cwprintf_s_l —](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|Zapis sformatowanych danych do konsoli|
|[_cputs —](../c-runtime-library/reference/cputs-cputws.md)|Zapisz ciąg do konsoli|
|[_cscanf —, _cwscanf —](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md), [_cscanf_s —, _cscanf_s_l —, _cwscanf_s —, _cwscanf_s_l —](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|Odczyt sformatowanych danych z konsoli|
|[_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)|Znak odczytu z konsoli|
|[_getche, _getwche](../c-runtime-library/reference/getch-getwch.md)|Odczytywanie znaków z konsoli i echo go|
|[_inp —](../c-runtime-library/inp-inpw-inpd.md)|Odczyt jednego bajtu z określonego portu We/Wy|
|[_inpd —](../c-runtime-library/inp-inpw-inpd.md)|Odczytaj o podwójnej precyzji word z określonego portu We/Wy|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|Określony port We/Wy odczytu word 2-bajtowych|
|[_kbhit](../c-runtime-library/reference/kbhit.md)|Sprawdź, czy naciśnięcie klawisza konsoli; Użyj przed podjęciem próby odczytu z konsoli|
|[_outp —](../c-runtime-library/outp-outpw-outpd.md)|Określony port We/Wy zapisu jednego bajtu|
|[_outpd —](../c-runtime-library/outp-outpw-outpd.md)|Określony port We/Wy zapisu word o podwójnej precyzji|
|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|Określony port We/Wy zapisu programu word|
|[_putch, _putwch](../c-runtime-library/reference/putch-putwch.md)|Wpisz znak do konsoli|
|[_ungetch —, _ungetwch —](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)|"Unget" ostatni znak staje się ona następny znak do odczytu do odczytu z konsoli|

## <a name="see-also"></a>Zobacz też

[Dane wejściowe i wyjściowe](../c-runtime-library/input-and-output.md)<br/>
 [Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>