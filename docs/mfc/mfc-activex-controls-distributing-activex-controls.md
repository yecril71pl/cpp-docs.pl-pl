---
title: 'Kontrolki ActiveX MFC: Dystrybucja kontrolek ActiveX'
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
ms.openlocfilehash: 409ace2197396cf7adbd330cfbd891745a23cf53
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300127"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>Kontrolki ActiveX MFC: Dystrybucja kontrolek ActiveX

W tym artykule omówiono kilka problemów związanych z redystrybuowanie kontrolek ActiveX:

- [ANSI lub Unicode kontroli wersji](#_core_ansi_or_unicode_control_versions)

- [Instalowanie kontrolek ActiveX i redystrybucyjnych bibliotek DLL](#_core_installing_activex_controls_and_redistributable_dlls)

- [Rejestrowanie formantów](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które zastępują ActiveX zobacz [formantów ActiveX](activex-controls.md).

##  <a name="_core_ansi_or_unicode_control_versions"></a> ANSI lub Unicode kontroli wersji

Należy określić, czy do wysłania ANSI lub Unicode wersja kontrolki i / lub. Ta decyzja opiera się na przenośność czynniki związane z zestawów znaków ANSI i Unicode.

Formanty ANSI, które działają we wszystkich systemach operacyjnych Win32, umożliwiają uzyskania maksymalnej przenośności między różnymi systemami operacyjnymi Win32. Formanty Unicode działa na tylko Windows NT (w wersji 3.51 lub nowszej), ale nie na Windows 95 lub Windows 98. Jeśli przenoszenia jest podstawową kwestią, dostarczaj ANSI kontrolki. Jeżeli kontrolkom będzie uruchamiany tylko na Windows NT, mogą być formanty Unicode. Można również wysłać zarówno i utworzyć swoją aplikację, zainstaluj wersję najbardziej odpowiedni dla systemu operacyjnego użytkownika.

##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> Instalowanie kontrolek ActiveX i redystrybucyjnych bibliotek DLL

Program instalacyjny, podane z formantów ActiveX należy utworzyć specjalne podkatalogiem katalogu Windows i zainstalować kontrolek. OCX w nim plików.

> [!NOTE]
>  Użyj Windows `GetWindowsDirectory` interfejsu API w programie Instalatora, aby uzyskać nazwę katalogu Windows. Można uzyskać nazwy podkatalogu na podstawie nazwy firmy lub produktu.

Program instalacyjny, należy zainstalować wymagane pliki redystrybucyjne biblioteki DLL w katalogu systemu Windows. Jeśli dowolny z biblioteki DLL jest już obecny na komputerze użytkownika, program instalacyjny należy porównać ich wersje z wersjami, którą instalujesz. Tylko wtedy, gdy jego numer wersji jest wyższy niż plik, który został już zainstalowany, zainstaluj ponownie plik.

Ponieważ formantów ActiveX może być używana tylko w aplikacje kontenera OLE, nie ma potrzeby dystrybucję pełny zestaw bibliotek DLL OLE przy użyciu kontrolki. Można założyć, że zawierającego aplikację (lub sam system operacyjny) ma standardowy OLE biblioteki DLL zainstalowane.

##  <a name="_core_registering_controls"></a> Rejestrowanie formantów

Przed użyciem formantu odpowiednie wpisy należy utworzyć dla niego w bazie danych rejestracji Windows. Niektóre kontenery kontrolek ActiveX, podaj element menu dla użytkowników zarejestrować nowe kontrolki, ale ta funkcja nie może być dostępny w wszystkich kontenerów. W związku z tym można program instalacyjny, aby Zarejestruj kontrolki, gdy są one zainstalowane.

Jeśli wolisz, możesz napisać program instalacyjny, aby zarejestrować formantu bezpośrednio zamiast tego.

Użyj `LoadLibrary` interfejsu API Windows, aby załadować formantu biblioteki DLL. Następnie użyj `GetProcAddress` można uzyskać adresu funkcji "DllRegisterServer". Na koniec Wywołaj `DllRegisterServer` funkcji. W poniższym przykładzie kodu pokazano jedną metodę możliwe, gdzie `hLib` przechowuje dojście Biblioteka kontrolek i `lpDllEntryPoint` przechowuje adresu funkcji "DllRegisterServer".

[!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

Zaletą bezpośrednio rejestrowanie kontrolki jest konieczne do wywołania i ładowania oddzielny proces (to znaczy, REGSVR32), skracając czas instalacji. Ponadto ponieważ wewnętrzny proces rejestracji, program instalacyjny może obsługiwać błędy i nieprzewidziane sytuacjach lepsze niż proces zewnętrzny można.

> [!NOTE]
>  Zanim program instalacyjny instaluje formantu ActiveX, powinny wywoływać `OleInitialize`. Po zakończeniu działania programu instalacyjnego wywołania `OleUnitialize`. Zapewnia to, że OLE systemowych bibliotek DLL są w stanie odpowiednie do rejestrowania formantu ActiveX.

Należy zarejestrować MFCx0.DLL.

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
