---
title: Błąd PRJ0009 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: d02325504b04a13cd15dee0bd70891bf5a63b62e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192968"
---
# <a name="project-build-error-prj0009"></a>Błąd PRJ0009 kompilacji projektu

Nie można otworzyć dziennika kompilacji do zapisu.

**Upewnij się, że plik nie jest otwarty przez inny proces i nie jest chroniony przed zapisem.**

Po ustawieniu właściwości **Rejestrowanie kompilacji** na **wartość tak** i wykonaniu kompilacji lub odbudowy, C++ Wizualizacja nie mogła otworzyć dziennika kompilacji w trybie wyłączności.

Sprawdź ustawienia **rejestrowania kompilacji** , otwierając okno dialogowe **Opcje** (w menu **Narzędzia** kliknij polecenie **Opcje** ), a następnie wybierz opcję **kompilacja VC + +** w folderze **projekty** . Plik kompilacji ma nazwę BuildLog. htm i jest zapisywana w katalogu pośrednim $ (IntDir).

Możliwe przyczyny tego błędu:

- Są uruchamiane dwa procesy wizualizacji C++ i podjęto próbę skompilowania tej samej konfiguracji tego samego projektu jednocześnie.

- Plik dziennika kompilacji jest otwierany w procesie, który blokuje plik.

- Użytkownik nie ma uprawnienia do tworzenia pliku.

- Bieżący użytkownik nie ma dostępu do zapisu do pliku BuildLog. htm.
