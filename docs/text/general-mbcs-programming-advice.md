---
title: Ogólne porady dotyczące programowania MBSC
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
ms.openlocfilehash: 887387220105614eb3257f008ec601a6fc0adc18
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491184"
---
# <a name="general-mbcs-programming-advice"></a>Ogólne porady dotyczące programowania MBSC

Skorzystaj z następujących wskazówek:

- Aby zapewnić elastyczność, użyj makr w czasie wykonywania, `_tcschr` takich `_tcscpy` jak i, jeśli to możliwe. Aby uzyskać więcej informacji, zobacz [Mapowanie tekstu ogólnego w używanie TCHAR. h](../text/generic-text-mappings-in-tchar-h.md).

- Użyj funkcji C Run-Time `_getmbcp` , aby uzyskać informacje o bieżącej stronie kodowej.

- Nie używaj ponownie zasobów ciągu. W zależności od języka docelowego dany ciąg może mieć inne znaczenie podczas tłumaczenia. Na przykład "plik" w menu głównym aplikacji może być w różny sposób przetłumaczony od ciągu "plik" w oknie dialogowym. Jeśli musisz użyć więcej niż jednego ciągu o tej samej nazwie, użyj innych identyfikatorów ciągów dla każdej z nich.

- Warto dowiedzieć się, czy aplikacja działa w systemie operacyjnym z obsługą MBCS. Aby to zrobić, Ustaw flagę przy uruchamianiu programu; nie należy polegać na wywołaniach interfejsu API.

- Podczas projektowania okien dialogowych, Zezwól na około 30% dodatkowego miejsca na końcu kontrolek tekstowych statycznych na potrzeby tłumaczenia MBCS.

- Należy zachować ostrożność podczas wybierania czcionek dla aplikacji, ponieważ niektóre czcionki nie są dostępne we wszystkich systemach.

- Podczas wybierania czcionki dla okien dialogowych, użyj okna programu [MS Shell](/windows/win32/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2) zamiast MS Sans Serif lub Helvetica. Okno dialogowe programu MS Shell jest zastępowane poprawną czcionką przez system przed utworzeniem okna dialogowego. Za pomocą okna programu MS Shell należy zapewnić, że wszelkie zmiany wprowadzone w systemie operacyjnym z tą czcionką będą automatycznie dostępne. (MFC zastępuje okno programu MS Shell DEFAULT_GUI_FONT lub czcionką systemową w systemach Windows 95, Windows 98 i Windows NT 4, ponieważ te systemy nie obsługują prawidłowo okna programu MS Shell).

- Podczas projektowania aplikacji Zdecyduj, które ciągi mogą być lokalizowane. W razie wątpliwości należy założyć, że każdy określony ciąg zostanie zlokalizowany. W związku z tym nie należy mieszać ciągów, które mogą być lokalizowane za pomocą tych, które nie mogą.

## <a name="see-also"></a>Zobacz także

[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)<br/>
[Inkrementacja i dekrementacja wskaźników](../text/incrementing-and-decrementing-pointers.md)
