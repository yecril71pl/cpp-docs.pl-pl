---
title: /SUBSYSTEM
ms.date: 11/04/2016
f1_keywords:
- /subsystem_editbin
helpviewer_keywords:
- /SUBSYSTEM editbin option
- -SUBSYSTEM editbin option
- SUBSYSTEM editbin option
ms.assetid: 515e4cdf-3cc4-4659-8764-1f2757b49215
ms.openlocfilehash: 708bfcce3e6d6616116bcc08441f374b46914c82
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438861"
---
# <a name="subsystem"></a>/SUBSYSTEM

Określa środowisko wykonywania wymagane przez obraz wykonywalny.

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
        EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|
        NATIVE|POSIX|WINDOWS|WINDOWSCE}[,major[.minor]]
```

## <a name="remarks"></a>Uwagi

Ta opcja umożliwia edycję obrazu w celu wskazania, który podsystem musi zostać wywołany przez system operacyjny w celu wykonania.

Można określić dowolne z następujących podsystemów:

**BOOT_APPLICATION**<br/>
Aplikacja działająca w środowisku rozruchu systemu Windows. Aby uzyskać więcej informacji na temat aplikacji rozruchowych, zobacz [Informacje o dostawcy WMI BCD](/previous-versions/windows/desktop/bcd/about-bcd).

**KONSOLI**<br/>
Aplikacja w trybie znakowym systemu Windows. System operacyjny udostępnia konsolę aplikacji konsolowych.

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
Obraz Extensible Firmware Interface (EFI)

Opcje podsystemu EFI opisują obrazy wykonywalne, które działają w środowisku Extensible Firmware Interface. To środowisko jest zwykle dostarczane z sprzętem i wykonywane przed załadowaniem systemu operacyjnego. Główne różnice między typami obrazów EFI są lokalizacją pamięci, do której obraz jest ładowany, i akcją wykonywaną po powrocie wywołania obrazu. Obraz EFI_APPLICATION zostanie zwolniony po powrocie kontroli. EFI_BOOT_SERVICE_DRIVER lub EFI_RUNTIME_DRIVER jest zwalniane tylko wtedy, gdy sterowanie zwraca kod błędu. Obraz EFI_ROM jest wykonywany z pamięci ROM. Aby uzyskać więcej informacji, zapoznaj się ze specyfikacjami w witrynie [ujednoliconego forum interfejsu EFI](https://www.uefi.org/) .

**TRYBU**<br/>
Kod, który jest uruchamiany bez środowiska podsystemu — na przykład sterowniki urządzeń trybu jądra i procesy systemu macierzystego. Ta opcja jest zwykle zarezerwowana dla funkcji systemu Windows.

**POSIX**<br/>
Aplikacja działająca w podsystemie POSIX w systemie Windows.

**Systemy**<br/>
Aplikacja działająca w środowisku graficznym systemu Windows. Dotyczy to zarówno aplikacji klasycznych, jak i aplikacji platforma uniwersalna systemu Windows (platformy UWP).

**WINDOWSCE**<br/>
Podsystem WINDOWSCE wskazuje, że aplikacja jest przeznaczona do uruchamiania na urządzeniu z wersją jądra Windows CE. Wersje jądra obejmują PocketPC, Windows Mobile, Windows Phone 7, Windows CE V 1.0 — 6.0 R3 i Windows Embedded Compact 7.

Opcjonalne `major` i `minor` określają minimalną wymaganą wersję określonego podsystemu:

- Liczba całkowita części numeru wersji — część po lewej stronie przecinka dziesiętnego — jest reprezentowana przez `major`.

- Część ułamkowa numeru wersji — część z prawej strony punktu dziesiętnego — jest reprezentowana przez `minor`.

- Wartości `major` i `minor` muszą zawierać się w zakresie od 0 do 65 535.

Wybór podsystemu wpływa na domyślny adres początkowy programu. Aby uzyskać więcej informacji, zobacz [/entry (symbol punktu wejścia)](entry-entry-point-symbol.md), konsolidator/entry:*Funkcja* .

Aby uzyskać więcej informacji, w tym wartości minimalne i domyślne dla głównych i pomocniczych numerów wersji dla każdego podsystemu, zobacz [/Subsystem](subsystem-specify-subsystem.md) -opcja konsolidatora.

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](editbin-options.md)
