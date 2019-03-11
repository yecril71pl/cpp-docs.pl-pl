---
title: Uruchamianie jako członek grupy użytkowników
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
- VCD0047
helpviewer_keywords:
- Users Group [C++]
- security [C++], Users Group
- Windows accounts [C++]
- non administrator users [C++]
- user accounts [C++]
- administrator (not running as) [C++]
ms.assetid: e48a03ec-d345-49f6-809a-1a291eecbc81
ms.openlocfilehash: dc06e2dc58d28c34a646ccffc0be90368b3297f5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747037"
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

## <a name="see-also"></a>Zobacz także

[Najlepsze rozwiązania dotyczące zabezpieczeń](security-best-practices-for-cpp.md)
