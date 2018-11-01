---
title: Błąd PRJ0009 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: 963b7c861f9e8ee7105ebdc23afff08c4be46465
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438106"
---
# <a name="project-build-error-prj0009"></a>Błąd PRJ0009 kompilacji projektu

Tworzenie dziennika nie może zostać otwarty do zapisu.

**Upewnij się, że plik nie jest otwarty przez inny proces i nie jest zabezpieczony przed zapisem.**

Po ustawieniu **kompilacji rejestrowania** właściwości **tak** i wykonywanie, tworzenie lub odbudowywanie, Visual C++ nie można otworzyć dziennika kompilacji w trybie wyłączności.

Sprawdzanie **kompilacji rejestrowania** ustawienie, otwierając **opcje** okno dialogowe (na **narzędzia** menu, kliknij przycisk **opcje** polecenie) a następnie Wybieranie **kompilacji VC ++** w **projektów** folderu. Plik kompilacji nosi nazwę BuildLog.htm i jest zapisywany w katalogu pośrednim $ (IntDir).

Możliwe przyczyny tego błędu:

- Są uruchomione dwa procesy Visual C++ i chcesz utworzyć taką samą konfigurację tego samego projektu w obu jednocześnie.

- Plik dziennika kompilacji zostanie otwarty w procesie, który blokuje go.

- Użytkownik nie ma uprawnień do utworzenia pliku.

- Bieżący użytkownik ma dostęp do zapisu do pliku nazwę BuildLog.htm.