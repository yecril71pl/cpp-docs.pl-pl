---
title: Uruchamianie jako członek grupy użytkowników
ms.date: 11/04/2016
helpviewer_keywords:
- Users Group [C++]
- security [C++], Users Group
- Windows accounts [C++]
- non administrator users [C++]
- user accounts [C++]
- administrator (not running as) [C++]
ms.assetid: e48a03ec-d345-49f6-809a-1a291eecbc81
ms.openlocfilehash: 117ef426950fc9aff5ae41e894f0d7ae898369cd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445444"
---
# <a name="running-as-a-member-of-the-users-group"></a>Uruchamianie jako członek grupy użytkowników

W tym temacie wyjaśniono, jak skonfigurować konta użytkowników systemu Windows jako członek grupy użytkowników (w przeciwieństwie do grupy administratorów) zwiększa bezpieczeństwo, zmniejszając prawdopodobieństwo zainfekowania złośliwego kodu.

## <a name="security-risks"></a>Zagrożenia bezpieczeństwa

Uruchomienie programu jako administrator sprawia, że system jest narażony na kilka rodzajów ataków zabezpieczeń, takich jak "koń trojański" i "przepełnienie buforu". Tylko odwiedzanie witryny internetowej jako administrator może być szkodliwe dla systemu, ponieważ złośliwy kod pobrany z witryny internetowej może zaatakować komputer. Jeśli to się powiedzie, dziedziczy uprawnienia administratora i może wykonywać takie działania, jak usuwanie wszystkich plików, ponowne formatowanie dysku twardego i tworzenie nowych kont użytkowników z dostępem administracyjnym.

## <a name="non-administrator-user-groups"></a>Grupy użytkowników niebędących administratorami

Konta użytkowników systemu Windows, których deweloperzy używają normalnie, powinny być dodawane do grup Użytkownicy lub Użytkownicy zaawansowani. Deweloperzy powinni również dodać do grupy debugowania. Będąc członkiem grupy Użytkownicy, można wykonywać rutynowe zadania, w tym uruchamiać programy i odwiedzać witryny internetowe bez narażania komputera o niepotrzebne ryzyko. Jako członek grupy Użytkownicy zaawansowani można także wykonywać zadania, takie jak instalacja aplikacji, instalacja drukarki i większość operacji w panelu sterowania. Jeśli konieczne jest wykonanie zadań administracyjnych, takich jak Uaktualnianie systemu operacyjnego lub Konfigurowanie parametrów systemowych, należy zalogować się do konta administratora przez wystarczająco długo, aby można było wykonać zadanie administracyjne. Alternatywnie można użyć polecenia **Uruchom jako** systemu Windows do uruchomienia określonych aplikacji z dostępem administracyjnym.

## <a name="exposing-customers-to-security-risks"></a>Ujawnianie klientom zagrożeń bezpieczeństwa

Administratorzy nie są częścią grupy administratorów, ponieważ oprócz ochrony maszyn programistycznych uniemożliwia deweloperom przypadkowe pisanie kodu, który wymaga od klientów dołączenia do grupy administratorów w programie Aby wykonać opracowywane aplikacje. Jeśli kod, który wymaga dostępu administratora jest wprowadzany podczas opracowywania, zakończy się niepowodzeniem w czasie wykonywania i zostanie wysłany alert informujący o tym, że aplikacja wymaga od klientów uruchamiania jako administratorów.

## <a name="code-that-requires-administrator-privileges"></a>Kod wymagający uprawnień administratora

Aby można było wykonać jakiś kod, wymagany jest dostęp administratora. Jeśli to możliwe, należy wykonać alternatywy dla tego kodu. Przykłady operacji kodu, które wymagają dostępu administratora, to:

- Zapisywanie w chronionych obszarach systemu plików, takich jak katalogi plików systemu Windows lub programu

- Zapisywanie w chronionych obszarach rejestru, takich jak HKEY_LOCAL_MACHINE

- Instalowanie zestawów w globalnej pamięci podręcznej zestawów (GAC)

Ogólnie rzecz biorąc, te działania powinny być ograniczone do programów instalacyjnych aplikacji. Dzięki temu użytkownicy mogą tylko tymczasowo korzystać z stanu administratora.

## <a name="debugging"></a>Debugowanie

Można debugować wszystkie aplikacje uruchamiane w programie Visual Studio (natywny i niezarządzany) jako niebędące administratorami, stając się częścią grupy debugowania. Obejmuje to możliwość dołączania do uruchomionej aplikacji przy użyciu polecenia Dołącz do procesu. Należy jednak być częścią grupy administratorów, aby debugować natywne lub zarządzane aplikacje, które zostały uruchomione przez innego użytkownika.

## <a name="see-also"></a>Zobacz też

[Najlepsze rozwiązania w zakresie zabezpieczeń](security-best-practices-for-cpp.md)
