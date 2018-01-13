---
title: -SUBSYSTEM | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /subsystem
dev_langs: C++
helpviewer_keywords:
- /SUBSYSTEM editbin option
- -SUBSYSTEM editbin option
- SUBSYSTEM editbin option
ms.assetid: 515e4cdf-3cc4-4659-8764-1f2757b49215
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f42efd011dfe5938eb455c885c6aa2c458910dfa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="subsystem"></a>/SUBSYSTEM
Określa środowiska wykonawczego, który jest wymagany przez obrazu wykonywalnego.  
  
```  
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|  
        EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|  
        NATIVE|POSIX|WINDOWS|WINDOWSCE}[,major[.minor]]  
```  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja służy do edytowania obrazu, aby wskazać, który podsystemu systemu operacyjnego należy wywołać do wykonania.  
  
 Można określić jedną z następujących podsystemów:  
  
 BOOT_APPLICATION  
 Aplikacja jest uruchamiana w środowisku rozruchu systemu Windows. Aby uzyskać więcej informacji na temat aplikacji rozruchu, zobacz[o dostawcę WMI BCD](http://msdn.microsoft.com/library/aa362639.aspx).  
  
 KONSOLI  
 Tryb znakowy aplikacji systemu Windows. System operacyjny udostępnia konsoli dla aplikacji konsoli.  
  
 Extensible Firmware Interface (EFI) obrazu  
 Opcje podsystemu EFI opisano obrazy wykonywalne, które są uruchamiane w środowisku Extensible Firmware Interface. To środowisko jest zwykle zapewniany ze sprzętem i jest wykonywana przed system operacyjny został załadowany. Najważniejsze różnice między EFI typy obrazów są lokalizacji obrazu jest ładowany do pamięci i akcję, która jest wykonywana po powrocie z wywołania do obrazu. Obraz EFI_APPLICATION jest zwolniony, po powrocie z formantu. EFI_BOOT_SERVICE_DRIVER lub EFI_RUNTIME_DRIVER jest zwolniony tylko wtedy, gdy formant zwraca kod błędu. Obraz EFI_ROM jest wykonywana w pamięci ROM. Aby uzyskać więcej informacji, zobacz specyfikacje na [Unified EFI Forum](http://www.uefi.org/) witryny sieci Web.  
  
 NATYWNY  
 Kod uruchamiany bez środowiska podsystemu — na przykład sterowników urządzenia trybu jądra i procesów systemowych macierzystego. Ta opcja jest zarezerwowany dla funkcji systemu Windows.  
  
 POSIX  
 Aplikacja jest uruchamiana w podsystemie POSIX w systemie Windows.  
  
 SYSTEMU WINDOWS  
 Aplikacja jest uruchamiana w środowisku graficznym systemu Windows. Obejmuje to zarówno aplikacji klasycznych i aplikacji ze Sklepu Windows.  
  
 WINDOWSCE  
 Podsystem WINDOWSCE wskazuje, że aplikacja jest przeznaczona do uruchamiania na urządzeniu, które ma wersję jądra systemu Windows CE. Wersje jądra zawierają urządzenia PocketPC, Windows Mobile, Windows Phone 7, Windows CE w wersji 1.0 6.0R3 i Windows Embedded Compact 7.  
  
 Opcjonalny `major` i `minor` wartości określają minimalnej wymaganej wersji podsystemu określony:  
  
-   Liczbę całkowitą część numeru wersji — części z lewej strony punktu dziesiętnego — jest reprezentowana przez `major`.  
  
-   Ułamkową część numeru wersji — części z prawej strony punktu dziesiętnego — jest reprezentowana przez `minor`.  
  
-   Wartości `major` i `minor` musi być z zakresu od 0 do 65 535.  
  
 Wybór podsystemu wpływa na domyślne początkowy adres dla programu. Aby uzyskać więcej informacji, zobacz [/Entry (Symbol punktu wejścia)](../../build/reference/entry-entry-point-symbol.md), konsolidatora/Entry:*funkcja* opcji.  
  
 Aby uzyskać więcej informacji, w tym minimum i domyślne wartości dla numerów wersji głównej i pomocniczej dla każdego podsystemu zobacz [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) — opcja konsolidatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje EDITBIN](../../build/reference/editbin-options.md)