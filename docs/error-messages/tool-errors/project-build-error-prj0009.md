---
title: Błąd PRJ0009 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0009
dev_langs:
- C++
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: efeb110823e801dd86a503a7069c4898f400769e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057187"
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