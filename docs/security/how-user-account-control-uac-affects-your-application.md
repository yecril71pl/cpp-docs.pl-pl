---
title: Jak kontrola konta użytkownika (UAC) wpływa na aplikację?
ms.date: 11/19/2018
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
ms.openlocfilehash: 8c283e86a71092bb510892b6361f3d0fddc2abb6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510143"
---
# <a name="how-user-account-control-uac-affects-your-application"></a>Jak kontrola konta użytkownika (UAC) wpływa na aplikację?

Kontrola konta użytkownika (UAC) to funkcja systemu Windows Vista, w której konta użytkowników mają ograniczone uprawnienia. Szczegółowe informacje na temat funkcji Kontrola konta użytkownika można znaleźć w następujących lokacjach:

- [Najlepsze rozwiązania i wskazówki dla deweloperów dotyczące aplikacji w środowisku najmniej uprzywilejowanym](/windows/win32/uxguide/winenv-uac)

## <a name="building-projects-after-enabling-uac"></a>Kompilowanie projektów po włączeniu funkcji Kontrola konta użytkownika

W przypadku tworzenia projektu programu Visual C++ Studio w systemie Windows Vista z wyłączeniem funkcji Kontrola konta użytkownika i włączeniu funkcji Kontrola konta użytkownika należy wyczyścić i ponownie skompilować projekt, aby działał poprawnie.

## <a name="applications-that-require-administrative-privileges"></a>Aplikacje wymagające uprawnień administracyjnych

Domyślnie konsolidator wizualny C++ osadza fragment kontroli konta użytkownika w manifeście aplikacji z poziomem `asInvoker`wykonania. Jeśli aplikacja wymaga uprawnień administracyjnych do prawidłowego działania (na przykład jeśli modyfikuje węzeł HKLM rejestru lub zapisuje je w chronionych obszarach dysku, takich jak katalog systemu Windows), należy zmodyfikować aplikację.

Pierwsza opcja polega na zmodyfikowaniu fragmentu UAC manifestu w celu zmiany poziomu wykonywania na *wymaga administratora*. Następnie aplikacja będzie monitować użytkownika o poświadczenia administracyjne przed jego uruchomieniem. Aby uzyskać informacje o tym, jak to zrobić, zobacz [/MANIFESTUAC (osadza informacje UAC w manifeście)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md).

Druga opcja polega na tym, że nie można osadzić fragmentu UAC w manifeście przez `/MANIFESTUAC:NO` określenie opcji konsolidatora. W takim przypadku aplikacja zostanie uruchomiona Zwirtualizowana. Wszelkie zmiany wprowadzone w rejestrze lub w systemie plików nie będą zachowywane po zakończeniu Twojej aplikacji.

Poniższy schemat blokowy opisuje sposób działania aplikacji w zależności od tego, czy funkcja Kontrola konta użytkownika jest włączona, oraz czy aplikacja ma manifest UAC:

![Zachowanie modułu ładującego systemu Windows](media/uacflowchart.png "Zachowanie modułu ładującego systemu Windows")

## <a name="see-also"></a>Zobacz także

[Najlepsze rozwiązania w zakresie zabezpieczeń](security-best-practices-for-cpp.md)
