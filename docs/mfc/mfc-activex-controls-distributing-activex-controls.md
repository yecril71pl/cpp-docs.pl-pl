---
title: 'Kontrolki ActiveX MFC: dystrybucja kontrolek ActiveX'
ms.date: 09/12/2018
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
helpviewer_keywords:
- MFC ActiveX controls [MFC], ANSI or Unicode versions
- RegSvr32.exe
- MFC ActiveX controls [MFC], distributing
- distributing MFC ActiveX controls
- redistributable files, MFC ActiveX controls
- GetSystemDirectory method [MFC]
- registering ActiveX controls
- MSVCRT40.dll
- registry [MFC], registering controls
- LoadLibrary method, registering ActiveX controls
- MFC40U.DLL
- MFC40.DLL
- GetWindowsDirectory method [MFC]
- installing ActiveX controls
- GetProcAddress method, registering ActiveX controls
- MFC ActiveX controls [MFC], installing
- MFC ActiveX controls [MFC], registering
- registering controls
- OLEPRO32.DLL
ms.assetid: cd70ac9b-f613-4879-9e81-6381fdfda2a1
ms.openlocfilehash: 11d647922a4f8097e03e112c0c93c833524c2c4e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618205"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>Kontrolki ActiveX MFC: dystrybucja kontrolek ActiveX

W tym artykule omówiono kilka problemów związanych z redystrybucją formantów ActiveX:

- [Wersje kontrolne ANSI lub Unicode](#_core_ansi_or_unicode_control_versions)

- [Instalowanie formantów ActiveX i redystrybucyjnych bibliotek DLL](#_core_installing_activex_controls_and_redistributable_dlls)

- [Rejestrowanie kontrolek](#_core_registering_controls)

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a>Wersje kontrolne ANSI lub Unicode

Należy zdecydować, czy ma być wysyłana wersja ANSI lub Unicode, czy obu. Ta decyzja jest oparta na czynnikach przenośności, które są związane z zestawami znaków ANSI i Unicode.

Formanty ANSI, które działają we wszystkich systemach operacyjnych Win32, umożliwiają maksymalne przenoszenie portów między różnymi systemami operacyjnymi Win32. Formanty Unicode działają tylko w systemie Windows NT (w wersji 3,51 lub nowszej), ale nie w systemie Windows 95 lub Windows 98. Jeśli przenośność stanowi podstawowe zagadnienie, Wyślij formanty ANSI. Jeśli kontrolki będą uruchamiane tylko w systemie Windows NT, można wydać formanty Unicode. Możesz również wybrać opcję dostarczania aplikacji i zainstalowania jej jako wersji odpowiedniej dla systemu operacyjnego użytkownika.

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a>Instalowanie formantów ActiveX i redystrybucyjnych bibliotek DLL

Program instalacyjny udostępniany z kontrolkami ActiveX powinien utworzyć specjalny podkatalog katalogu systemu Windows i zainstalować formanty. Pliki OCX.

> [!NOTE]
> Użyj `GetWindowsDirectory` interfejsu API systemu Windows w programie instalacyjnym, aby uzyskać nazwę katalogu systemu Windows. Można utworzyć nazwę podkatalogu na podstawie nazwy firmy lub produktu.

Program instalacyjny musi zainstalować wymagane pliki DLL redystrybucyjnych w katalogu systemu Windows. Jeśli dowolna z bibliotek dll znajduje się już na komputerze użytkownika, program instalacyjny powinien porównać ich wersje z instalowanymi wersjami. Zainstaluj ponownie plik tylko wtedy, gdy jego numer wersji jest wyższy niż plik już zainstalowany.

Ponieważ kontrolki ActiveX mogą być używane tylko w aplikacjach kontenera OLE, nie ma potrzeby dystrybucji pełnego zestawu bibliotek DLL OLE z kontrolkami. Można założyć, że aplikacja zawierająca (lub system operacyjny) ma zainstalowane standardowe biblioteki DLL OLE.

## <a name="registering-controls"></a><a name="_core_registering_controls"></a>Rejestrowanie kontrolek

Aby można było użyć kontrolki, należy dla niej utworzyć odpowiednie wpisy w bazie danych rejestracji systemu Windows. Niektóre kontenery kontrolek ActiveX udostępniają element menu użytkownikom do rejestrowania nowych kontrolek, ale ta funkcja może nie być dostępna we wszystkich kontenerach. W związku z tym możesz chcieć, aby program instalacyjny zarejestrował formanty po ich zainstalowaniu.

Jeśli wolisz, możesz napisać program instalacyjny, aby w zamian zarejestrować formant bezpośrednio.

Użyj `LoadLibrary` interfejsu API systemu Windows do załadowania biblioteki DLL kontroli. Następnie użyj elementu, `GetProcAddress` Aby uzyskać adres funkcji "DllRegisterServer". Na koniec Wywołaj `DllRegisterServer` funkcję. Poniższy przykład kodu ilustruje jedną możliwą metodę, gdzie `hLib` przechowuje dojście biblioteki formantów i `lpDllEntryPoint` przechowuje adres funkcji "DllRegisterServer".

[!code-cpp[NVC_MFC_AxCont#16](codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

Zalety rejestrowania kontroli bezpośrednio polegają na tym, że nie trzeba wywoływać i ładować oddzielnego procesu (tj. REGSVR32), skracając czas instalacji. Ponadto, ponieważ rejestracja jest procesem wewnętrznym, program instalacyjny może obsłużyć błędy i nieprzewidziane sytuacje lepiej niż proces zewnętrzny.

> [!NOTE]
> Przed zainstalowaniem formantu ActiveX przez program instalacyjny powinien zostać wywołany `OleInitialize` . Po zakończeniu działania programu instalacyjnego Wywołaj polecenie `OleUnitialize` . Zapewnia to, że biblioteki DLL systemu OLE są w odpowiednim stanie do rejestrowania kontrolki ActiveX.

Należy zarejestrować MFCx0. DLL.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
