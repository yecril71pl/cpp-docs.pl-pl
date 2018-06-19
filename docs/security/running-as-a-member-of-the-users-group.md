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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4faeae9100cf6e60a2eeda19baea20ba42be197f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841663"
---
# <a name="running-as-a-member-of-the-users-group"></a>Uruchamianie jako członek grupy użytkowników
W tym temacie opisano sposób konfigurowania konta użytkownika systemu Windows jako członek grupy Użytkownicy (w przeciwieństwie do grupy Administratorzy) zwiększa bezpieczeństwo, zmniejsza ryzyko jest zainfekowany złośliwym kodem.  
  
## <a name="security-risks"></a>Zagrożenia bezpieczeństwa  
 Uruchomiona jako administrator sprawia, że system jest narażony na kilka rodzajów atak na zabezpieczenia, takie jak "Koń trojański" i "przepełnienie buforu". Jedynie zaproszonych witryny internetowej jako administrator może uszkodzić system, jako złośliwy kod, który jest pobierany z witryny internetowej może ataku komputera. W przypadku powodzenia dziedziczy uprawnienia administratora i może następnie wykonuje działania takie jak usunąć wszystkie pliki, ponownego formatowania dysku twardego i tworzenia nowego użytkownika konta z dostępem administracyjnym.  
  
## <a name="non-administrator-user-groups"></a>Grupy użytkowników z systemem innym niż administratora  
 Kont użytkowników systemu Windows, które deweloperzy normalnie z niego korzystać należy dodać do użytkowników lub grup użytkowników zasilania. Deweloperzy również należy dodać do grupy debugowanie. Będąc członkiem grupy Użytkownicy służy do wykonywania rutynowych zadań, w tym wykonywania programów i odwiedzania witryn internetowych bez narażania komputera niepotrzebnie. Jako członek grupy Użytkownicy zaawansowani mogą też wykonywać zadania, takie jak instalowanie aplikacji, instalacja drukarki i większość operacji panelu sterowania. Jeśli potrzebujesz do wykonywania zadań administracyjnych, takich jak uaktualnianie systemu operacyjnego lub skonfigurowanie parametrów systemu, należy rejestrować do konta administratora długo tylko do wykonywania zadań administracyjnych. Alternatywnie Windows **runas** polecenia może służyć do uruchamiania aplikacji określonego z dostępem administracyjnym.  
  
## <a name="exposing-customers-to-security-risks"></a>Udostępnianie klientom na zagrożenia bezpieczeństwa  
 Nie jest częścią grupy Administratorzy jest szczególnie ważne dla deweloperów, ponieważ, oprócz ochrony programowanie maszyny, uniemożliwia deweloperzy mogą przypadkowo pisania kodu wymaga, aby dołączyć do grupy Administratorzy klienci Aby wykonać aplikacje się, że w przypadku tworzenia. Jeśli podczas opracowywania wprowadzono kod, który wymaga dostępu administratora, zakończy się niepowodzeniem w czasie wykonywania, wysyłać alerty o fakt, że teraz aplikacja wymaga klientów do uruchamiania jako administratorzy.  
  
## <a name="code-that-requires-administrator-privileges"></a>Kod, który wymaga uprawnień administratora  
 Kodu wymaga dostępu administratora, aby wykonać. Jeśli to możliwe należy dążyć alternatywy dla tego kodu. Przykłady kodu operacji, które wymagają dostępu administratora:  
  
-   Zapisywanie w chronionych obszarach systemu plików, takich jak Windows lub Program Files katalogów  
  
-   Zapisywanie do rejestru, takie jak HKEY_LOCAL_MACHINE chronionych obszarach  
  
-   Instalowanie zestawów w globalnej pamięci podręcznej zestawów (GAC)  
  
 Ogólnie rzecz biorąc działania te należy ograniczyć do programy instalacyjne aplikacji. To pozwala użytkownikom na używanie tylko tymczasowo stan administratora.  
  
## <a name="debugging"></a>Debugowanie  
 Można debugować wszystkie aplikacje, które będzie uruchomić w programie Visual Studio (natywny i niezarządzane) z systemem innym niż administrator przez staje się częścią grupy debugowanie. Obejmuje to możliwość dołączenia uruchomioną aplikację przy użyciu dołączanie do procesu polecenia. Jednak należy należeć do grupy administratorów w celu debugowania natywnego lub zarządzanego aplikacji, które zostały uruchomione przez innego użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Najlepsze rozwiązania](security-best-practices-for-cpp.md)