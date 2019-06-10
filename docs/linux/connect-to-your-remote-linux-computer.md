---
title: Nawiązywanie zdalnego komputer z systemem Linux w programie Visual Studio
description: Jak połączyć się z komputera zdalnego systemu Linux z wewnątrz projektu Visual Studio C++.
ms.date: 06/07/2019
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: 6348681ecc8e6f7863b2119810db24879526a1c6
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821611"
---
# <a name="connect-to-your-remote-linux-computer"></a>Nawiązywanie połączenia ze zdalnym komputerem z systemem Linux

::: moniker range="vs-2015"

Pomoc techniczna Linux support jest dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

::: moniker range="vs-2019"

Gdy docelowego podsystemu Windows dla systemu Linux (WSL) programu Visual Studio korzysta z Twojego dystrybucja systemu Linux bezpośrednio za pomocą systemu plików; niezbędne jest nie połączenia zdalnego.

::: moniker-end

Podczas kompilowania C++ projektu systemu Linux dla systemu Linux systemu zdalnego (maszyny Wirtualnej lub komputera fizycznego), Linux, kod jest kopiowany do komputera zdalnego systemu Linux, a następnie kompilowane zgodnie z ustawieniami programu Visual Studio. Aby skonfigurować tego połączenia zdalnego:

1. Skompiluj projekt po raz pierwszy, albo ręcznie utworzyć nowy wpis, wybierając **Narzędzia > Opcje** , a następnie otwórz **wiele Platform > Menedżer połączeń** węzła i kliknij przycisk **Dodaj** przycisku.

   ![Menedżer połączeń](media/settings_connectionmanager.png)

   W dowolnym scenariuszu **nawiązywanie połączenia z systemem zdalnym** zostanie wyświetlone okno.

   ![Łączenie z systemem zdalnym](media/connect.png)

1. Wprowadź następujące informacje:

   | Wpis | Opis
   | ----- | ---
   | **Nazwa hosta**           | Nazwa lub adres IP urządzenia docelowego
   | **Port**                | Port, czy usługa SSH jest uruchomiona na ogół 22
   | **Nazwa użytkownika**           | Użytkownika do uwierzytelnienia się jako
   | **Typ uwierzytelniania** | Hasło lub klucz prywatny są obsługiwane
   | **Hasło**            | Hasło dla wprowadzona nazwa użytkownika
   | **Plik klucza prywatnego**    | Plik klucza prywatnego dla protokołu ssh połączenie utworzone
   | **Hasło**          | Hasło używane razem z kluczem prywatnym w wybranym powyżej

1. Kliknij przycisk **Connect** przycisk prób połączenia z komputerem zdalnym.  Jeśli połączenie nie powiedzie się, pola wpisu, które muszą zostać zmienione zostaną opisane w kolorze czerwonym.

   ![Błąd Menedżera połączeń](media/settings_connectionmanagererror.png)