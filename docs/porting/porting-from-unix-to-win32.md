---
title: Eksportowanie z systemu UNIX do Win32 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- APIs [C++], porting to Win32
- Windows API [C++], migrating from UNIX
- migration [C++]
- UNIX [C++], porting to Win32
- porting to Win32 [C++], from UNIX
- porting to Win32 [C++]
- Win32 applications [C++], migrating from UNIX
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 628d032ff00205b3f511a613a866f025d62dc50a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843291"
---
# <a name="porting-from-unix-to-win32"></a>Eksportowanie z systemu UNIX do Win32
Podczas migrowania aplikacji z systemu UNIX do systemu Windows, masz kilka opcji:  
  
-   Przy użyciu biblioteki systemu UNIX do portu aplikacji z systemu UNIX do Win32  
  
-   Natywnie eksportowanie aplikacji z systemu UNIX do Win32  
  
-   Uruchamianie aplikacji systemu UNIX w systemie Windows przy użyciu podsystemu POSIX  
  
## <a name="unix-libraries"></a>Biblioteki systemu UNIX  
 Jedną z opcji UNIX programistów zwykle należy wziąć pod uwagę umożliwi ich kompilacji kodu UNIX jako plik wykonywalny systemu Win32 za pomocą biblioteki systemu UNIX przypominającej innych firm. Kilka komercyjnej (i co najmniej jednej domeny publicznej) biblioteki w tym celu. Jest to opcja dla niektórych aplikacji. Korzystać z tych eksportowanie bibliotek jest, że ich zminimalizować ilość pracy od początkowego przenoszenia. Główną wadą produktu konkurencyjnych oprogramowania, jest zazwyczaj będzie szybsze portu natywnego Win32 aplikacji oraz będą mieć więcej funkcji. Może to być nieodpowiednich dla aplikacji, aby krok poza powłoki systemu UNIX, wymaga wykonywania wywołań Win32, aby uzyskać więcej mocy z systemu Windows.  
  
 Poniższa lista zawiera firmy Microsoft i innych firm zasobów dla przenoszenia i obsługę UNIX migracji do programu Visual C++:  
  
### <a name="unix-migration-guides"></a>Przewodniki migracji systemu UNIX  
 Przewodnik migracji aplikacji niestandardowe UNIX zawiera pomoc techniczną po migracji kodu z systemu UNIX do środowiska Win32.  
  
 [http://go.microsoft.com/fwlink/p/?linkid=95428](http://go.microsoft.com/fwlink/p/?linkid=95428)  
  
 Przewodnik po programie Project migracji Unix uzupełnia Przewodnik migracji aplikacji niestandardowe UNIX przez zapewnienie wysokiego poziomu pomocy w przypadku migrowania projektów znacznej z systemu UNIX do systemu Win32. Przewodnik zawiera wskazówki dotyczące zagadnień do uwzględnienia na każdym etapie migracji projektu. Przewodnik może zostać pobrana z:  
  
 [http://go.microsoft.com/fwlink/p/?linkid=20012](http://go.microsoft.com/fwlink/p/?linkid=20012)  
  
### <a name="microsoft-windows-services-for-unix-sfu"></a>Usługi systemu Microsoft Windows dla systemu UNIX (SFU)  
 Microsoft Windows Services dla systemu UNIX (SFU) udostępnia szeroką gamę między platformami usługi integracji systemu Windows w istniejących środowiskach systemu UNIX. Usługi dla systemu UNIX zapewnia udostępniania plików, dostępu zdalnego i administracji, synchronizacji haseł, wspólnego zarządzania katalogu, ze wspólnego zestawu narzędzi i powłoki.  
  
 [Usługi systemu Windows dla systemu UNIX](http://www.microsoft.com/downloads/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en)  
  
### <a name="interopsystemscom"></a>InteropSystems.com  
 [http://www.interopsystems.com/](http://www.interopsystems.com/)  
  
 Inna witryna firmy zapewnienie programów obsługi przenoszenia systemu UNIX do Win32.  
  
### <a name="c-boost-web-site"></a>Zwiększanie wyniku C++ witryny sieci Web  
 [http://boost.sourceforge.net/regression-logs/](http://boost.sourceforge.net/regression-logs/)  
  
 [http://boost.sourceforge.net/boost-build2/](http://boost.sourceforge.net/boost-build2/)  
  
## <a name="porting-unix-applications-directly-to-win32"></a>Eksportowanie aplikacji systemu UNIX bezpośrednio do systemu Win32  
 Inną opcją jest przenoszenie aplikacji systemu UNIX bezpośrednio do systemu Win32. Przy użyciu biblioteki ANSI C/C++ i komercyjnych biblioteki kompilatora C, wiele tradycyjnego systemu wywołania zależał od aplikacji systemu UNIX są dostępne w aplikacji Win32.  
  
 Model danych wyjściowych **stdio —**-aplikacji nie musi zostać zmienione od czasu konsoli Win32 API naśladować **stdio —** modelu i wersje *curses* istnieje używające konsoli Win32 API. Aby uzyskać więcej informacji, zobacz [SetConsoleCursorPosition](http://msdn.microsoft.com/library/windows/desktop/ms686025).  
  
 Aplikacje oparte na gniazdo Berkeley muszą bardzo kilka zmian w pracy aplikacji Win32. Interfejsu Windows Sockets zostało zaprojektowane na potrzeby przenośność z gniazda BSD, przy minimalnych zmianach, które są wymienione w sekcji wprowadzenie specyfikacji interfejsu WinSock.  
  
 System Windows obsługuje zgodne DCE RPC, tak więc łatwo można używać aplikacji opartych na RPC. Zobacz [funkcji RPC](http://msdn.microsoft.com/library/windows/desktop/aa378623).  
  
 Jest jednym z największych obszarów różnicy w modelu procesów. Ma UNIX **rozwidlenia**; Nie ma Win32. W zależności od użycia **rozwidlenia** i bazowej kodu Win32 ma dwa interfejsy API, które mogą być używane: **CreateProcess** i `CreateThread`. Aplikacji systemu UNIX, który rozwidlenia wiele kopii samego można ponownie obrobione, w systemie Win32 wiele procesów lub jeden proces o wiele wątków. Jeśli wiele procesów są używane, istnieje wiele metod IPC, który może służyć do komunikacji między procesami (i prawdopodobnie można zaktualizować kodu i danych nowy proces, na przykład element nadrzędny, jeśli funkcji który **rozwidlenia** udostępnia jest potrzebny). Aby uzyskać więcej informacji na temat IPC, zobacz [komunikacji międzyprocesowej](http://msdn.microsoft.com/library/windows/desktop/aa365574).  
  
 Systemu Windows i UNIX graficznego modeli są bardzo różnią się. UNIX używa X GUI systemu Windows, gdy system Windows używa interfejsu GDI. Chociaż jest to podobna, nie ma mapowania prostego interfejsu API X do interfejsu API interfejsu GDI. Jednak OpenGL obsługa jest dostępna dla migracji aplikacji OpenGL systemu UNIX. Jednak X klientów i X serwerów dla systemu Windows. Zobacz [konteksty urządzenia](http://msdn.microsoft.com/library/windows/desktop/dd183553) dla informacji na temat interfejsu GDI.  
  
 Podstawowe aplikacje systemu UNIX, w tym wiele aplikacji CGI, powinien łatwo portu dla Visual C++ z systemem Windows. Funkcji, takich jak **Otwórz**, `fopen`, **odczytu**, **zapisu** , a inne są dostępne w bibliotece środowiska wykonawczego Visual C++. Ponadto istnieje mapowanie jeden do jednego między interfejsów API systemu UNIX C i Win32 API: **Otwórz** do **CreateFile**, **odczytu** do **ReadFile**, **zapisu** do **WriteFile**, `ioctl` do **DeviceIOControl**, **zamknąć** do **CloseFile**i tak dalej.  
  
## <a name="windows-posix-subsystem"></a>Podsystem POSIX w systemie Windows  
 Inną opcję UNIX programistów przyjrzeć jest podsystemu POSIX w systemie Windows. Jednak tylko obsługuje 1003.1 POSIX, która była tylko wersji POSIX standaryzowane podczas tworzenia systemu Windows NT. Od tego czasu wprowadzono niewielkie wymagania dotyczące rozszerzania tego podsystemu ponieważ większość aplikacji zostały przekonwertowane do systemu Win32. 1003.1 systemu jest ograniczone istotnych dla wszystkich funkcji aplikacji, ponieważ nie zawiera wiele funkcji (takich jak te w 1003.2 obsługi sieci i tak dalej). Pełna polecanych aplikacji uruchamiana z podsystem POSIX w systemie Windows nie mają dostępu do funkcji systemu Windows, dostępne dla aplikacji Win32, takich jak pliki mapowane w pamięci, sieci i grafiki. Aplikacje, takie jak VI, LS i GREP są elementy docelowe głównej podsystemu POSIX w systemie Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Visual C++, przenoszenie i uaktualnianie przewodnik](visual-cpp-change-history-2003-2015.md)   
 [UNIX](../c-runtime-library/unix.md)   
 [Zasady wnioskowania](../build/inference-rules.md)