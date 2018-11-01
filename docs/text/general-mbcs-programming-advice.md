---
title: Ogólne porady dotyczące programowania MBSC
ms.date: 11/04/2016
f1_keywords:
- _mbcs
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
ms.openlocfilehash: 0ff15244f4e93ecd2913fa825e8b5c351c7ff84d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501845"
---
# <a name="general-mbcs-programming-advice"></a>Ogólne porady dotyczące programowania MBSC

Użyj następujących wskazówek:

- Elastyczność, użyj makra w czasie wykonywania takich jak `_tcschr` i `_tcscpy` gdy jest to możliwe. Aby uzyskać więcej informacji, zobacz [mapowania typ ogólny-tekst w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md).

- Użyj środowiska wykonawczego języka C `_getmbcp` funkcję, aby uzyskać informacje o bieżącej stronie kodowej.

- Nie należy używać ponownie zasoby w postaci ciągów. W zależności od języka docelowego ciągu może mieć inne znaczenie podczas translacji. Na przykład menu "File" w aplikacji w usłudze głównego może tłumaczyć inaczej od ciągu "File" w oknie dialogowym. Jeśli potrzebujesz więcej niż jednego ciągu za pomocą tej samej nazwie, użyj ciągu różne identyfikatory dla każdego.

- Możesz chcieć sprawdzić, czy aplikacja jest uruchomiona w systemie operacyjnym włączone MBCS. Aby to zrobić, należy ustawić flagę w momencie uruchamiania programu; nie należy polegać na wywołania interfejsu API.

- Podczas projektowania okna dialogowe, Zezwalaj na około 30% dodatkowe miejsce na końcu statyczny tekst kontrolki do tłumaczenia MBCS.

- Należy zachować ostrożność, wybierając czcionki dla aplikacji, ponieważ niektóre czcionki nie są dostępne we wszystkich systemach.

- Podczas wybierania czcionek dla okien dialogowych, użyj [MS Shell Dlg](/windows/desktop/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2) zamiast MS Serif sieci SAN lub Helvetica. MS Shell Dlg zastępuje z poprawną czcionką systemu przed utworzeniem okna dialogowego. Korzystanie z MS Shell Dlg zapewnia, wszelkie zmiany w systemie operacyjnym, aby poradzić sobie w tej czcionce będą automatycznie dostępne. (MFC zastępuje MS Shell Dlg DEFAULT_GUI_FONT lub czcionki systemowej na Windows 95, Windows 98 i Windows NT 4, ponieważ te systemy nie obsługują MS Shell Dlg poprawnie).

- Podczas projektowania aplikacji, należy zdecydować, ciągi, które może być lokalizowana. W razie wątpliwości założono zostanie zlokalizowany wszelkie dany ciąg znaków. Jako takie nie należy mieszać ciągów, które może być lokalizowana z tymi, które nie.

## <a name="see-also"></a>Zobacz też

[Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)<br/>
[Inkrementacja i dekrementacja wskaźników](../text/incrementing-and-decrementing-pointers.md)