---
title: Rejestracja
ms.date: 11/04/2016
helpviewer_keywords:
- servers [MFC], initializing
- initializing servers [MFC]
- OLE, registration
- installing servers [MFC]
- registry [MFC], OLE item database
- registration databases [MFC]
- servers [MFC], installing
- OLE server applications [MFC], registering servers
ms.assetid: 991d5684-72c1-4f9e-a09a-9184ed12bbb9
ms.openlocfilehash: 82411e53620e92eff3484f7d3f7955030fd439ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372838"
---
# <a name="registration"></a>Rejestracja

Gdy użytkownik chce wstawić element OLE do aplikacji, OLE przedstawia listę typów obiektów do wyboru. Ole pobiera tę listę z bazy danych rejestracji systemu, która zawiera informacje dostarczone przez wszystkie aplikacje serwera. Gdy serwer rejestruje się, wpisy, które umieszcza w bazie danych rejestracji systemu (Rejestru) opisują każdy typ obiektu, który dostarcza, rozszerzenia plików i ścieżkę do siebie, wśród innych informacji.

Struktura i biblioteki dynamiczne łącza dynamicznego systemu OLE (DLL) używają tego rejestru do określenia, jakie typy elementów OLE są dostępne w systemie. Biblioteki DLL systemu OLE również używać tego rejestru, aby określić, jak uruchomić aplikację serwera, gdy obiekt połączony lub osadzony jest aktywowany.

W tym artykule opisano, co każda aplikacja serwera musi zrobić, gdy jest zainstalowany i za każdym razem, gdy jest wykonywany.

Aby uzyskać szczegółowe informacje na temat bazy danych rejestracji systemu i formatu plików .reg użytych do jej aktualizacji, zobacz *odwołanie programisty OLE*.

## <a name="server-installation"></a><a name="_core_server_installation"></a>Instalacja serwera

Podczas pierwszej instalacji aplikacji serwera, należy zarejestrować wszystkie typy elementów OLE, które obsługuje. Można również zaktualizować serwer bazy danych rejestracji systemu za każdym razem, gdy jest wykonywana jako aplikacja autonomiczna. Dzięki temu baza danych rejestracji jest aktualna, jeśli plik wykonywalny serwera zostanie przeniesiony.

> [!NOTE]
> Aplikacje MFC generowane przez kreatora aplikacji automatycznie rejestrują się, gdy są uruchamiane jako aplikacje autonomiczne.

Jeśli chcesz zarejestrować aplikację podczas instalacji, użyj programu RegEdit.exe. Jeśli do aplikacji zostanie dołączona program instalacyjny, należy uruchomić program instalacyjny "RegEdit /S *appname*.reg". (Flaga /S wskazuje cichą operację, oznacza to, że nie wyświetla okna dialogowego raportowania pomyślnego wykonania polecenia.) W przeciwnym razie poinstruuj użytkownika, aby uruchamiał program RegEdit ręcznie.

> [!NOTE]
> Plik reg utworzony przez kreatora aplikacji nie zawiera pełnej ścieżki dla pliku wykonywalnego. Program instalacyjny musi zmodyfikować plik reg, aby uwzględnić pełną ścieżkę do pliku wykonywalnego lub zmodyfikować zmienną środowiskową PATH w celu uwzględnienia katalogu instalacyjnego.

RegEdit scala zawartość pliku tekstowego .reg z bazą danych rejestracji. Aby zweryfikować bazę danych lub ją naprawić, użyj edytora rejestru. Należy uważać, aby uniknąć usuwania podstawowych wpisów OLE.

## <a name="server-initialization"></a><a name="_core_server_initialization"></a>Inicjowanie serwera

Podczas tworzenia aplikacji serwera za pomocą kreatora aplikacji kreator automatycznie wypełnia wszystkie zadania inicjalizacji. W tej sekcji opisano, co należy zrobić, jeśli piszesz aplikację serwera ręcznie.

Gdy aplikacja serwera jest uruchamiana przez aplikację kontenera, biblioteki DLL systemu OLE dodają opcję "/Osadzanie" do wiersza polecenia serwera. Zachowanie aplikacji serwera różni się w zależności od tego, czy został uruchomiony przez kontener, więc pierwszą rzeczą, którą aplikacja powinna zrobić, gdy rozpoczyna wykonywanie jest sprawdzenie opcji "/Osadzanie" lub "-Osadzanie" w wierszu polecenia. Jeśli ten przełącznik istnieje, załaduj inny zestaw zasobów, które pokazują, że serwer jest aktywny w miejscu lub w pełni otwarty. Aby uzyskać więcej informacji, zobacz [Menu i zasoby: Dodatki do serwera](../mfc/menus-and-resources-server-additions.md).

Aplikacja serwera powinna również `CWinApp::RunEmbedded` wywołać jego funkcję, aby przeanalizować wiersz polecenia. Jeśli zwraca wartość niezerową, aplikacja nie powinna wyświetlać swojego okna, ponieważ została ona uruchomiony z aplikacji kontenera, a nie jako aplikacja autonomiczna. Ta funkcja aktualizuje wpis serwera w bazie danych `RegisterAll` rejestracji systemu i wywołuje funkcję elementu członkowskiego, wykonując rejestrację wystąpienia.

Po uruchomieniu aplikacji serwera należy upewnić się, że może ona wykonywać rejestrację wystąpienia. Rejestracja wystąpienia informuje biblioteki DLL systemu OLE, że serwer jest aktywny i gotowy do odbierania żądań z kontenerów. Nie dodaje wpisu do bazy danych rejestracji. Wykonaj rejestrację wystąpienia serwera, `ConnectTemplate` wywołując funkcję `COleTemplateServer`elementu członkowskiego zdefiniowaną przez program . Spowoduje to `CDocTemplate` połączenie obiektu `COleTemplateServer` z obiektem.

Funkcja `ConnectTemplate` przyjmuje trzy parametry: *identyfikator CLSID*serwera, `CDocTemplate` wskaźnik do obiektu i flagę wskazującą, czy serwer obsługuje wiele wystąpień. Miniserwer musi być w stanie obsługiwać wiele wystąpień, oznacza to, że musi być możliwe dla wielu wystąpień serwera do uruchamiania jednocześnie, po jednym dla każdego kontenera. W związku z tym, przekazać **TRUE** dla tej flagi podczas uruchamiania miniserver.

Jeśli piszesz miniserwer, z definicji zawsze będzie uruchamiany przez kontener. Należy nadal przeanalizować wiersz polecenia, aby sprawdzić, czy opcja "/Osadzanie". Brak tej opcji w wierszu polecenia oznacza, że użytkownik próbował uruchomić miniserwer jako samodzielną aplikację. W takim przypadku zarejestruj serwer w bazie danych rejestracji systemu, a następnie wyświetl okno komunikatu informujące użytkownika o uruchomieniu miniserweru z aplikacji kontenera.

## <a name="see-also"></a>Zobacz też

[OLE](../mfc/ole-in-mfc.md)<br/>
[Serwery](../mfc/servers.md)<br/>
[CWinApp::UruchomAutoma](../mfc/reference/cwinapp-class.md#runautomated)<br/>
[CWinApp::RunEmbedded](../mfc/reference/cwinapp-class.md#runembedded)<br/>
[Klasa COleTemplateServer](../mfc/reference/coletemplateserver-class.md)
