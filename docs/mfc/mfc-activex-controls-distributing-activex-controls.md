---
title: 'Formanty MFC ActiveX: Dystrybucja formantów ActiveX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c6658c972b9d9cdeececd43a89ac424964d2289
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>Kontrolki ActiveX MFC: dystrybucja kontrolek ActiveX
W tym artykule opisano kilka problemów związanych z redystrybuowanie formantów ActiveX:  
  
-   [ANSI lub Unicode kontroli wersji](#_core_ansi_or_unicode_control_versions)  
  
-   [Instalowanie formantów ActiveX i pakietu redystrybucyjnego bibliotek DLL](#_core_installing_activex_controls_and_redistributable_dlls)  
  
-   [Rejestrowanie formantów](#_core_registering_controls)  
  
##  <a name="_core_ansi_or_unicode_control_versions"></a> ANSI lub Unicode kontroli wersji  
 Należy określić, czy należy wysłać wersji ANSI lub Unicode, lub obie. Ta decyzja zależy od przenośność czynniki związane z zestawów znaków ANSI i Unicode.  
  
 Formanty ANSI, które działa we wszystkich systemach operacyjnych Win32, umożliwiają maksymalny przenoszenia między różnymi systemami operacyjnymi Win32. Formanty Unicode działają w tylko systemu Windows NT (wersja 3.51 lub nowsza), ale nie w systemie Windows 95 lub Windows 98. Jeśli przenośność jest najważniejszą kwestią, wysyłki ANSI kontrolki. Jeżeli formantów będzie uruchamiany tylko w systemie Windows NT, mogą być formanty Unicode. Można również wybrać zarówno wysyłki i aplikacja, zainstaluj wersję najbardziej odpowiednie dla systemu operacyjnego użytkownika.  
  
##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> Instalowanie formantów ActiveX i pakietu redystrybucyjnego bibliotek DLL  
 Instalator zapewniają z formantów ActiveX powinien tworzenia specjalnych podkatalogu w katalogu systemu Windows i zainstaluj kontrolki. OCX w nim plików.  
  
> [!NOTE]
>  Użyj okna **GetWindowsDirectory** interfejsu API programu Instalatora można uzyskać nazwy katalogu systemu Windows. Można uzyskać nazwy podkatalogu z nazwy firmy lub produktu.  
  
 Instalator musi zainstalować niezbędnych plików DLL pakietu redystrybucyjnego w katalogu systemu Windows. Jeśli którekolwiek z bibliotek DLL są już występuje na komputerze użytkownika, program instalacyjny należy porównać ich wersje z wersjami, którą instalujesz. Tylko wtedy, gdy jej numer wersji jest wyższy niż plik już zainstalowany, zainstaluj ponownie plik.  
  
 Ponieważ formantów ActiveX może być używana tylko w aplikacje kontenera OLE, jest niepotrzebna do dystrybucji pełny zestaw biblioteki DLL OLE z formantów. Można Załóżmy, że zawierającego aplikacji (lub systemu operacyjnego, sam) zawiera standardowe OLE bibliotek DLL zainstalowane.  
  
##  <a name="_core_registering_controls"></a> Rejestrowanie formantów  
 Przed użyciem formantu odpowiednie wpisy należy utworzyć dla niego w bazie danych rejestracji systemu Windows. Niektóre kontenery formantów ActiveX Podaj element menu dla użytkowników zarejestrować nowe formanty, ale ta funkcja może nie być dostępne na wszystkich kontenerów. W związku z tym można z Instalatora, aby zarejestrować formanty, kiedy są instalowane.  
  
 Jeśli wolisz, możesz zapisywać Twoje Instalatora, aby zarejestrować formant bezpośrednio zamiast tego.  
  
 Użyj **LoadLibrary** załadować formantu DLL interfejsu API systemu Windows. Następnie użyj **GetProcAddress** uzyskać adresu funkcji "DllRegisterServer". Na koniec wywołania `DllRegisterServer` funkcji. Poniższy przykładowy kod przedstawia jedną metodę możliwe, gdy `hLib` przechowuje dojście Biblioteka kontrolek i `lpDllEntryPoint` przechowuje adresu funkcji "DllRegisterServer".  
  
 [!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]  
  
 Zaletą bezpośrednio rejestrowanie kontrolki jest konieczne do wywołania i załadować oddzielnych procesach (to znaczy, REGSVR32), skracając czas instalacji. Ponadto ponieważ wewnętrzny proces rejestracji, program instalacyjny można obsługi błędów i lepszym rozwiązaniem niż procesu zewnętrznego nieprzewidzianych sytuacjach można.  
  
> [!NOTE]
>  Zanim program Instalator zainstaluje formantu ActiveX, należy wywołać **Funkcja OleInitialize**. Po zakończeniu instalacji programu wywołać **OleUnitialize**. To rozwiązanie zapewnia OLE systemowej biblioteki dll do prawidłowego stanu rejestrowania formantów ActiveX.  
  
 Należy zarejestrować MFCx0.DLL.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

