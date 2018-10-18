---
title: Nawiązywanie zdalnego komputer z systemem Linux w programie Visual Studio | Dokumentacja firmy Microsoft
description: Jak połączyć się z komputera zdalnego systemu Linux z wewnątrz projektu Visual Studio C++.
ms.custom: ''
ms.date: 07/20/2018
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 5e6a5dd4a00bd4d98c36222434d7cd83242905c9
ms.sourcegitcommit: db6b2ad3195e71abfb60b62f3f015f08b0a719d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410762"
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