---
title: Łączenie się z komputerem zdalnym systemu Linux | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/06/2017
ms.technology:
- cpp-linux
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: dd7f73a01b3b0941144ff59a683a9e42467f5a18
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="connect-to-your-remote-linux-computer"></a>Łączenie się z komputerem zdalnym systemu Linux

Podczas kompilowania, kod systemu Linux jest kopiowany do komputera zdalnego systemu Linux, a następnie skompilowany w tym systemie zgodnie z ustawieniami w programie Visual Studio.  Do instalacji tego połączenia zdalnego:

1. Skompiluj projekt po raz pierwszy lub ręcznie utwórz nowy wpis wybierając **Narzędzia > Opcje** , a następnie otwórz **Cross Platform > Menedżera połączeń** węzeł i kliknij przycisk **Dodaj** przycisku.

   ![Menedżera połączeń](media/settings_connectionmanager.png)

   W każdym z tych scenariuszy **Połącz z systemu zdalnego** będzie wyświetlane okno.
   
   ![Połącz do systemu zdalnego](media/connect.png)

1. Wprowadź następujące informacje:

   | Wpis | Opis
   | ----- | ---
   | **Nazwa hosta**           | Nazwa lub adres IP urządzenia docelowego
   | **Port**                | Port, czy usługa SSH jest uruchomiona na zwykle 22
   | **Nazwa użytkownika**           | Uwierzytelnienia jako użytkownika
   | **Typ uwierzytelniania** | Hasła lub klucza prywatnego są obsługiwane
   | **Hasło**            | Hasło dla wprowadzona nazwa użytkownika
   | **Plik klucza prywatnego**    | Wygenerowany klucz prywatny dla ssh połączenia
   | **Hasło**          | Hasło używane z kluczem prywatnym wybranej powyżej

1. Kliknij przycisk **Connect** przycisk prób połączenia z komputerem zdalnym.  Jeśli połączenie nie powiedzie się, pola wejścia, które muszą zostać zmienione zostaną podane w czerwony.

   ![Błąd Menedżera połączeń](media/settings_connectionmanagererror.png)