---
title: Ogólne programowania Mbsc | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc27d0b0396fed6e6b03f6c3f8e1f2332fcceecf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421105"
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