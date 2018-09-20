---
title: Uruchamianie jako członek grupy Użytkownicy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- PRJ0050
- VCD0047
dev_langs:
- C++
helpviewer_keywords:
- Users Group [C++]
- security [C++], Users Group
- Windows accounts [C++]
- non administrator users [C++]
- user accounts [C++]
- administrator (not running as) [C++]
ms.assetid: e48a03ec-d345-49f6-809a-1a291eecbc81
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34028aa243f4c767751da758e43dab5ecf71c110
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431804"
---
# <a name="running-as-a-member-of-the-users-group"></a>Uruchamianie jako członek grupy użytkowników

W tym temacie opisano sposób konfigurowania kont użytkowników Windows jako członek grupy Użytkownicy (w przeciwieństwie do grupy Administratorzy) zwiększa bezpieczeństwo, zmniejszając prawdopodobieństwo jest zainfekowany złośliwym kodem.

## <a name="security-risks"></a>Zagrożenia bezpieczeństwa

Uruchomione jako administrator sprawia, że system jest narażony na kilka rodzajów atak na zabezpieczenia, takie jak "Koń trojański" i "przepełnienie buforu". Jedynie zaproszonych witryny internetowej jako administrator może uszkodzić system, jako złośliwy kod, który jest pobierany z witryny internetowej może ataku komputera. W przypadku powodzenia dziedziczy uprawnienia administratora, a następnie można wykonać akcje, takie jak usuwanie wszystkich plików, ponownego formatowania dysku twardego i tworzenia konta nowego użytkownika z dostępem administracyjnym.

## <a name="non-administrator-user-groups"></a>Grupy użytkowników innych niż Administrator

Konta użytkowników Windows, które deweloperzy normalnie z niego korzystać, należy dodać do użytkowników lub grup użytkowników usługi Power. Deweloperzy również należy dodać do grupy debugowanie. Są oni członkami grupy Użytkownicy umożliwia wykonywanie rutynowych zadań, w tym uruchamianie programów i odwiedzania witryn internetowych bez narażania komputera niepotrzebnie. Jako członek grupy Użytkownicy zaawansowani można również wykonać zadania, takie jak instalowanie aplikacji, instalacja drukarki i większość operacji panelu sterowania. Jeśli potrzebujesz do wykonywania zadań administracyjnych, takich jak uaktualnianie systemu operacyjnego lub skonfigurowanie parametrów systemu, możesz powinni logować się do konta administratora tak długo wystarczający do wykonywania zadań administracyjnych. Alternatywnie Windows **runas** polecenia mogą służyć do uruchamiania konkretnych aplikacji z dostępem administracyjnym.

## <a name="exposing-customers-to-security-risks"></a>Udostępnianie klientom na zagrożenia bezpieczeństwa

Nie jest częścią grupy Administratorzy jest szczególnie ważne dla deweloperów, ponieważ, oprócz ochrony na komputerach deweloperskich, uniemożliwia deweloperom przypadkowo pisanie kodu, który wymaga od klientów do dołączenia do grupy Administratorzy kolejność do wykonywania aplikacji Ci tworzyć. Jeśli kod, który wymaga dostępu administratora zostanie wprowadzona podczas tworzenia, zakończy się niepowodzeniem w czasie wykonywania, wysyłać alerty o fakt, że teraz Twoja aplikacja wymaga od klientów do uruchamiania jako administrator.

## <a name="code-that-requires-administrator-privileges"></a>Kod, który wymaga uprawnień administratora

Kod wymaga dostępu administratora do działania. Jeśli to możliwe należy dążyć alternatywy dla tego kodu. Przykłady operacji kodu, które wymagają dostępu administratora:

- Zapisywanie katalogów chronionych obszarach systemu plików, takich jak Windows lub Program Files

- Zapisywanie do rejestru, np. HKEY_LOCAL_MACHINE chronionych obszarach

- Instalowanie zestawów w globalnej pamięci podręcznej zestawów (GAC)

Ogólnie rzecz biorąc działania te powinny być ograniczone do programów instalacyjnych aplikacji. Dzięki temu użytkownicy mogą używać tylko tymczasowo stan administratora.

## <a name="debugging"></a>Debugowanie

Można debugować wszystkie aplikacje, które można uruchomić w programie Visual Studio (natywne i niezarządzane) jako użytkowników niebędących administratorami, staje się częścią grupy debugowanie. Obejmuje to możliwość dołączenia do uruchomionej aplikacji przy użyciu Dołącz do procesu polecenia. Jednakże należy być częścią grupy administratorów, aby debugować aplikacje natywne i zarządzane, które zostały uruchomione przez innego użytkownika.

## <a name="see-also"></a>Zobacz też

[Najlepsze rozwiązania dotyczące zabezpieczeń](security-best-practices-for-cpp.md)