---
title: Nawiązywanie zdalnego komputer z systemem Linux w programie Visual Studio
description: Jak połączyć się z komputera zdalnego systemu Linux z wewnątrz projektu Visual Studio C++.
ms.date: 07/20/2018
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
ms.openlocfilehash: ce6a3c02846586dbc46b0c9bc0db0d579878c814
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575246"
---
# <a name="connect-to-your-remote-linux-computer"></a>Podłącz do komputera zdalnego systemu Linux

Podczas kompilowania projektu systemu Linux w języku C++ w programie Visual Studio, Linux, kod jest kopiowany do komputera zdalnego systemu Linux, a następnie kompilowane zgodnie z ustawieniami programu Visual Studio. Aby skonfigurować tego połączenia zdalnego:

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