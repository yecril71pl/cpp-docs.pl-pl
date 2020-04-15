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
ms.openlocfilehash: 1ada1c801b2d9d62f1cc4cd5bf72a2995225b3de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364626"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>Kontrolki ActiveX MFC: dystrybucja kontrolek ActiveX

W tym artykule omówiono kilka kwestii związanych z redystrybucją formantów ActiveX:

- [Wersje ansi lub unicode control](#_core_ansi_or_unicode_control_versions)

- [Instalowanie formantów ActiveX i redystrybucyjnych bibliotek DLL](#_core_installing_activex_controls_and_redistributable_dlls)

- [Rejestrowanie formantów](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a>Wersje ansi lub unicode control

Należy zdecydować, czy wysłać ansi lub Unicode wersji formantu lub obu. Decyzja ta jest oparta na czynnikach przenośności nieodłącznie związanych z zestawami znaków ANSI i Unicode.

Formanty ANSI, które działają na wszystkich systemach operacyjnych Win32, pozwalają na maksymalną przenośność między różnymi systemami operacyjnymi Win32. Sterowanie unicode działa tylko w systemie Windows NT (wersja 3.51 lub nowsza), ale nie w systemie Windows 95 lub Windows 98. Jeśli przenośność jest twoim głównym problemem, należy wysłać elementy sterujące ANSI. Jeśli formanty będą działać tylko w systemie Windows NT, można wysłać formanty Unicode. Można również wybrać opcję wysyłki obu i mieć aplikację zainstalować wersję najbardziej odpowiednią dla systemu operacyjnego użytkownika.

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a>Instalowanie formantów ActiveX i redystrybucyjnych bibliotek DLL

Program instalacyjny udostępniany za pomocą formantów ActiveX powinien utworzyć specjalny podkatalog katalogu systemu Windows i zainstalować formanty. pliki OCX w nim.

> [!NOTE]
> Użyj interfejsu `GetWindowsDirectory` API systemu Windows w programie instalacyjnym, aby uzyskać nazwę katalogu systemu Windows. Nazwę podkatalogu można wyprowadzić od nazwy firmy lub produktu.

Program instalacyjny musi zainstalować niezbędne redystrybucyjne pliki DLL w katalogu systemu Windows. Jeśli którykolwiek z bibliotek DLL jest już obecny na komputerze użytkownika, program instalacyjny powinien porównać ich wersje z instalowaną wersją. Zainstaluj ponownie plik tylko wtedy, gdy jego numer wersji jest wyższy niż plik już zainstalowany.

Ponieważ formanty ActiveX mogą być używane tylko w aplikacjach kontenerów OLE, nie ma potrzeby dystrybucji pełnego zestawu bibliotek DLL OLE za pomocą formantów. Można założyć, że aplikacja zawierająca (lub sam system operacyjny) ma zainstalowane standardowe biblioteki DLL OLE.

## <a name="registering-controls"></a><a name="_core_registering_controls"></a>Rejestrowanie formantów

Aby można było użyć formantu, należy utworzyć odpowiednie wpisy w bazie danych rejestracji systemu Windows. Niektóre kontenery formantu ActiveX zapewniają element menu dla użytkowników, aby zarejestrować nowe formanty, ale ta funkcja może nie być dostępna we wszystkich kontenerach. W związku z tym można zarejestrować formanty podczas ich instalowania przez program instalacyjny.

Jeśli wolisz, możesz napisać program instalacyjny, aby zarejestrować formant bezpośrednio.

Użyj `LoadLibrary` interfejsu API systemu Windows, aby załadować bibliotekę DLL formantu. Następnie użyj, `GetProcAddress` aby uzyskać adres funkcji "DllRegisterServer". Na koniec wywołaj `DllRegisterServer` funkcję. Poniższy przykładowy kod pokazuje jedną `hLib` możliwą metodę, `lpDllEntryPoint` gdzie przechowuje dojście biblioteki formantu i przechowuje adres funkcji "DllRegisterServer".

[!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

Zaletą bezpośredniej rejestracji formantu jest to, że nie trzeba wywoływać i ładować oddzielny proces (a mianowicie REGSVR32), skracając czas instalacji. Ponadto, ponieważ rejestracja jest procesem wewnętrznym, program instalacyjny może obsługiwać błędy i nieprzewidziane sytuacje lepiej niż proces zewnętrzny.

> [!NOTE]
> Zanim program instalacyjny zainstaluje kontrolę ActiveX, należy wywołać . `OleInitialize` Po zakończeniu programu instalacyjnego zadzwoń do `OleUnitialize`programu . Gwarantuje to, że biblioteki DLL systemu OLE są w odpowiednim stanie do rejestrowania formantu ActiveX.

Należy zarejestrować mfcx0.DLL.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
