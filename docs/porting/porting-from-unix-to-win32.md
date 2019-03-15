---
title: Eksportowanie z systemu UNIX do Win32
ms.date: 08/02/2018
helpviewer_keywords:
- APIs [C++], porting to Win32
- Windows API [C++], migrating from UNIX
- migration [C++]
- UNIX [C++], porting to Win32
- porting to Win32 [C++], from UNIX
- porting to Win32 [C++]
- Win32 applications [C++], migrating from UNIX
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
ms.openlocfilehash: 325cdb86f61f658776c69057022c005c389492d3
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813906"
---
# <a name="porting-from-unix-to-win32"></a>Eksportowanie z systemu UNIX do Win32

Podczas migracji aplikacji z systemu UNIX do Windows, masz kilka opcji:

- Przy użyciu biblioteki systemu UNIX do portu aplikacji z systemu UNIX do Win32

- Przenoszenie aplikacji z systemu UNIX do Win32 natywnie

- Uruchamianie aplikacji systemu UNIX w Windows, za pomocą podsystemu POSIX

## <a name="unix-libraries"></a>Biblioteki systemu UNIX

Jedną z opcji UNIX programistów zwykle należy wziąć pod uwagę przy użyciu bibliotek podobnymi do systemu UNIX innych firm umożliwiające ich kompilacji kodu systemu UNIX jako plikiem wykonywalnym środowiska Win32. Wiele komercyjnych (i co najmniej jedną domenę publiczną) biblioteki to zrobić. Jest to opcja dla niektórych aplikacji. Te przenoszenie bibliotek zaletą jest to, że one zminimalizować początkowy przenoszenia. Główne wady, konkurencyjnych oprogramowania jest, zwykle krócej portu macierzystego systemu Win32 w aplikacji i będą mieć więcej funkcji. Może być nieodpowiednich dla aplikacji wkraczać poza powłoki systemu UNIX, wymaga wykonywania wywołań Win32, aby uzyskać więcej energii z Windows.

Na poniższej liście przedstawiono firmy Microsoft i innych zasobów przenoszenie i UNIX migrację do programu Visual C++:

### <a name="unix-migration-guides"></a>Przewodniki dotyczące migracji z systemu UNIX

[Przewodnik migracji aplikacji niestandardowych UNIX](https://technet.microsoft.com/library/bb656290.aspx) zapewnia pomoc techniczną na migrację kodu z systemu UNIX do środowiska Win32.

[Przewodnik projektu migracji Unix](https://technet.microsoft.com/library/bb656287.aspx) uzupełnia Przewodnik migracji aplikacji niestandardowego systemu UNIX, zapewniając wysokiego poziomu pomocy w przypadku migrowania projektów istotne z systemu UNIX do Win32. Przewodnik zawiera porady dotyczące zagadnień do uwzględnienia na każdym etapie migracji projektu.

### <a name="microsoft-windows-services-for-unix-sfu"></a>Program Microsoft Windows Services for UNIX (SFU)

Microsoft Windows Services for UNIX (SFU) zapewnia pełną gamę usług dla wielu platform zintegrować Windows istniejących środowisk opartych na systemie UNIX. Usługi dla systemu UNIX zapewnia udostępniania plików, dostępu zdalnego i administracji, synchronizacja haseł, wspólne zarządzanie katalogu, ze wspólnego zestawu narzędzi i powłoki.

[Windows Services for UNIX](http://www.microsoft.com/downloads/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en)

### <a name="interopsystemscom"></a>InteropSystems.com

[http://www.interopsystems.com/](http://www.interopsystems.com/)

Innej lokacji w firmie zapewnienie im programów obsługi przenoszenia systemu UNIX do Win32.

### <a name="c-boost-web-site"></a>C++ zwiększenie wydajności witryny sieci Web

[http://boost.sourceforge.net/regression-logs/](http://boost.sourceforge.net/regression-logs/)

[http://boost.sourceforge.net/boost-build2/](http://boost.sourceforge.net/boost-build2/)

## <a name="porting-unix-applications-directly-to-win32"></a>Przenoszenie aplikacji systemu UNIX bezpośrednio do systemu Win32

Innym rozwiązaniem jest przenoszenie aplikacji systemu UNIX bezpośrednio do systemu Win32. Przy użyciu biblioteki ANSI C/C++ i komercyjnych bibliotek kompilator C, wiele tradycyjny system, który wywołuje opiera się na aplikacji systemu UNIX są dostępne w aplikacji Win32.

Model danych wyjściowych **stdio —**-aplikacji nie musi zostać zmienione w stosunku konsoli Win32 API naśladować **stdio —** modelu i wersji *curses* istnieje używające konsoli Win32 API. Aby uzyskać więcej informacji, zobacz [SetConsoleCursorPosition](/windows/console/setconsolecursorposition).

Aplikacje oparte na gniazdo Berkeley muszą bardzo kilka zmian, aby pracować w aplikacji Win32. Interfejsu Windows Sockets został zaprojektowany do celów przenośności przy użyciu gniazd BSD, przy minimalnych zmianach, które zostały wymienione w sekcjach wprowadzające specyfikacji interfejsu WinSock.

Windows obsługuje CLS DCE RPC, tak aby łatwo można używać aplikacji opartego na protokole RPC. Zobacz [funkcji RPC](/windows/desktop/Rpc/rpc-functions).

Jest jednym z największych obszarów różnica w modelu procesów. Ma UNIX `fork`; Win32 — nie. W zależności od użycia `fork` i kodzie podstawowym, Win32 ma dwa interfejsy API, które mogą być używane: `CreateProcess` i `CreateThread`. Aplikacji systemu UNIX, który rozwidlenia wielu kopii sam można przekształcił w systemie Win32 wiele procesów lub jeden proces w wielu wątkach. Wiele procesów są używane, dostępnych jest wiele metod IPC, który może służyć do komunikacji między procesami (i prawdopodobnie aktualizowania kodu i danych nowego procesu jako element nadrzędny, np. Jeśli funkcjonalność, `fork` zapewnia jest potrzebny). Aby uzyskać więcej informacji o IPC, zobacz [komunikacji międzyprocesowej](/windows/desktop/ipc/interprocess-communications).

Windows i UNIX graficzny modeli są bardzo różne. UNIX używa X okna systemu graficznego interfejsu użytkownika, gdy Windows korzysta z użyciem interfejsu GDI. Chociaż jest to podobne, nie ma żadnych mapowania proste interfejsu API X do interfejsu API z użyciem interfejsu GDI. Jednak obsługa OpenGL jest dostępne do migracji aplikacji OpenGL systemu UNIX. Wiąże się z X klientów i X serwerów Windows. Zobacz [konteksty urządzenia](/windows/desktop/gdi/device-contexts) informacji z użyciem interfejsu GDI.

Podstawowe aplikacji systemu UNIX, w tym wiele aplikacji CGI, powinien portu łatwe do programu Visual C++ w systemie Windows. Funkcje, takie jak `open`, `fopen`, `read`, `write` i inne są dostępne w bibliotece środowiska wykonawczego Visual C++. Ponadto istnieje mapowanie jeden do jednego między interfejsów API systemu UNIX C i Win32: `open` do `CreateFile`, `read` do `ReadFile`, `write` do `WriteFile`, `ioctl` do `DeviceIOControl`, `close` do `CloseFile`i tak dalej.

## <a name="windows-posix-subsystem"></a>Podsystem Windows POSIX

Inną opcja UNIX programistów przyjrzeć to podsystemu Windows POSIX. Jednakże obsługuje on tylko 1003.1 POSIX, który jedynie wersja POSIX standaryzowane podczas tworzenia systemu Windows NT. Od tamtej pory nastąpiła nieco żądanie do ten podsystem rozszerzania, ponieważ większość aplikacji zostały przekonwertowane na Win32. 1003.1 system jest ograniczone znaczenie w odniesieniu do aplikacji w pełni wyposażone, ponieważ nie zawiera wiele funkcji (takich jak te w 1003.2 sieci pomocy technicznej i tak dalej). Pełne polecanych aplikacji uruchamiana z podsystem Windows POSIX nie mają dostępu do funkcji Windows, które są dostępne do aplikacji Win32, takich jak pliki mapowane w pamięci, sieci i grafiki. Aplikacje, takie jak VI, LS i GREP są główne cele podsystemu Windows POSIX.

## <a name="see-also"></a>Zobacz także

[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](visual-cpp-change-history-2003-2015.md)<br/>
[UNIX](../c-runtime-library/unix.md)<br/>
[Zasady wnioskowania](../build/reference/inference-rules.md)
