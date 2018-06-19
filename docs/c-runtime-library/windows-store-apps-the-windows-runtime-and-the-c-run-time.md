---
title: Aplikacji platformy uniwersalnej systemu Windows, środowiska uruchomieniowego systemu Windows i C Run-Time | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29e1a67ce57e4ddf726ba64923bbe5a95b5b2f1c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410843"
---
# <a name="uwp-apps-the-windows-runtime-and-the-c-run-time"></a>Aplikacji platformy uniwersalnej systemu Windows, środowiska uruchomieniowego systemu Windows i C Run-Time

Uniwersalnych aplikacji platformy systemu Windows (UWP) są programy, które działają w środowiska uruchomieniowego systemu Windows, która wykonuje na [!INCLUDE[win8](../build/reference/includes/win8_md.md)]. Środowisko wykonawcze systemu Windows jest wiarygodnego środowiska, która kontroluje, funkcje, zmienne i zasobów, które są dostępne dla aplikacji platformy uniwersalnej systemu Windows. Zgodnie z projektem ograniczenia środowiska wykonawczego systemu Windows uniemożliwić korzystanie z większości funkcji biblioteki wykonawcze języka C (CRT) w aplikacji platformy uniwersalnej systemu Windows.

Środowisko wykonawcze systemu Windows nie obsługuje następujące funkcje CRT:

- Większość funkcji CRT, które są powiązane z nieobsługiwanych funkcji.

   Na przykład aplikacji platformy uniwersalnej systemu Windows nie może utworzyć procesu za pomocą **exec** i **duplikowanie** rodzin procedury.

   Gdy funkcja CRT jest nieobsługiwana w aplikacji platformy uniwersalnej systemu Windows, że fakt znajdują się w artykule o jego.

- Najbardziej wielobajtowe funkcji znaków i ciąg.

   Jednak zarówno Unicode i ANSI tekst są obsługiwane.

- Aplikacje konsoli i argumenty wiersza polecenia.

   Tradycyjne aplikacje komputerowe nadal obsługuje jednak konsoli i argumenty wiersza polecenia.

- Zmienne środowiskowe.

- Pojęcie bieżący katalog roboczy.

- Platformy uniwersalnej systemu Windows aplikacji i bibliotek DLL, które statycznie połączone z CRT, utworzony za pomocą [/MT](../build/reference/md-mt-ld-use-run-time-library.md) lub `/MTd` — opcje kompilatora.

   Oznacza to, aplikacji, która korzysta z wielowątkowej, statycznej wersji CRT.

- Aplikację, która została skompilowana przy użyciu [/mdd](../build/reference/md-mt-ld-use-run-time-library.md) — opcja kompilatora.

   Oznacza to, debugowania, wielowątkowej i specyficznej dla biblioteki DLL środowiska CRT. Takie aplikacja nie jest obsługiwana na środowiska uruchomieniowego systemu Windows.

Pełną listę funkcji CRT, które nie są dostępne w aplikacji platformy uniwersalnej systemu Windows i sugestie dotyczące funkcji alternatywnych, zobacz [funkcje CRT, nie są obsługiwane w aplikacjach platformy uniwersalnej systemu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="see-also"></a>Zobacz też

[Zgodność](../c-runtime-library/compatibility.md)<br/>
[Nieobsługiwane funkcje CRT środowiska uruchomieniowego systemu Windows](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
