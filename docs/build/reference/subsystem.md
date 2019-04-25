---
title: /SUBSYSTEM
ms.date: 11/04/2016
f1_keywords:
- /subsystem
helpviewer_keywords:
- /SUBSYSTEM editbin option
- -SUBSYSTEM editbin option
- SUBSYSTEM editbin option
ms.assetid: 515e4cdf-3cc4-4659-8764-1f2757b49215
ms.openlocfilehash: b13313d57226719086cb73584543488f842057c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317721"
---
# <a name="subsystem"></a>/SUBSYSTEM

Określa środowisko wykonawcze, wymagane przez obraz uruchamiany.

```
/SUBSYSTEM:{BOOT_APPLICATION|CONSOLE|EFI_APPLICATION|
        EFI_BOOT_SERVICE_DRIVER|EFI_ROM|EFI_RUNTIME_DRIVER|
        NATIVE|POSIX|WINDOWS|WINDOWSCE}[,major[.minor]]
```

## <a name="remarks"></a>Uwagi

Ta opcja edytuje obraz, aby wskazać który podsystem musi zostać wywołany systemu operacyjnego do wykonania.

Można określić dowolny z poniższych podsystemów:

**BOOT_APPLICATION**<br/>
Aplikacja, która jest uruchamiana w środowisku Windows rozruchowego. Aby uzyskać więcej informacji dotyczących aplikacji rozruchu, zobacz [o dostawcy BCD WMI](/previous-versions/windows/desktop/bcd/about-bcd).

**KONSOLA**<br/>
Tryb znakowy aplikacji Windows. System operacyjny zapewnia konsolę dla aplikacji konsoli.

**EFI_APPLICATION**<br/>
**EFI_BOOT_SERVICE_DRIVER**<br/>
**EFI_ROM**<br/>
**EFI_RUNTIME_DRIVER**<br/>
Extensible Firmware Interface (EFI) obrazu

Opcje podsystemu EFI opisują wykonywalne obrazów, które działają w środowisku rozszerzalnego interfejsu oprogramowania układowego. To środowisko jest typowo wyposażone sprzęt i jest wykonywany przed załadowaniem systemu operacyjnego. Najważniejsze różnice między typami obrazów EFI są lokalizacji w pamięci, który obraz, który jest ładowany i akcję, która zostanie podjęta, gdy zwraca wywołanie do obrazu. Obraz EFI_APPLICATION jest zwolniony, gdy zwraca formant. EFI_BOOT_SERVICE_DRIVER lub EFI_RUNTIME_DRIVER jest zwalniany tylko wtedy, gdy formant zwraca kod błędu. Obraz EFI_ROM jest wykonywany z ROM. Aby uzyskać więcej informacji, zobacz specyfikację w witrynie [Unified EFI Forum](http://www.uefi.org/) witryny sieci Web.

**NATYWNE**<br/>
Kod, który jest uruchamiany bez środowiska podsystemu — na przykład sterowniki urządzeń trybu jądra i procesów systemu macierzystego. Ta opcja jest zazwyczaj zarezerwowana dla funkcji systemu Windows.

**POSIX**<br/>
Aplikacja, która działa w podsystemie POSIX w Windows.

**SYSTEMU WINDOWS**<br/>
Aplikacja, która działa w pśrodowisku graficznym Windows. Obejmuje to aplikacje pulpitu i aplikacje platformy uniwersalnej Windows (UWP).

**WINDOWSCE**<br/>
Podsystem WINDOWSCE oznacza, że aplikacja jest przeznaczony do uruchamiania na urządzeniu, które ma wersję jądra Windows CE. Wersje jądra obejmują PocketPC, Windows Mobile, Windows Phone 7, Windows CE V1.0-6.0R3 oraz Windows Embedded Compact 7.

Opcjonalny `major` i `minor` wartości określają minimalną wymaganą wersję określonego podsystemu:

- Cała część numeru wersji — część po lewej stronie przecinka dziesiętnego — jest reprezentowana przez `major`.

- Część ułamkowa numeru wersji — część po prawej stronie przecinka dziesiętnego — jest reprezentowana przez `minor`.

- Wartości `major` i `minor` musi być z zakresu od 0 do 65 535.

Wybór podsystemu wpływa na domyślny początkowy adres dla programu. Aby uzyskać więcej informacji, zobacz [/Entry (Symbol punktu wejścia)](entry-entry-point-symbol.md), konsolidatora/Entry:*funkcja* opcji.

Aby uzyskać więcej informacji, w tym wartościach minimalnych i domyślnych dla numerów wersji głównych i pomocniczych każdego podsystemu, zobacz [/Subsystem](subsystem-specify-subsystem.md) — opcja konsolidatora.

## <a name="see-also"></a>Zobacz także

[Opcje EDITBIN](editbin-options.md)
