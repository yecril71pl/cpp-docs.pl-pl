---
title: Rejestracja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e115edc4a7a276e04e886a0d7d324308dbe1c8ed
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399590"
---
# <a name="registration"></a>Rejestracja

Gdy użytkownik chce, aby wstawić element OLE do aplikacji, OLE wyświetla listę typów obiektów do wybrania. OLE pobiera tej listy z system bazy danych rejestracji, który zawiera informacje podane przez wszystkie aplikacje serwera. Gdy serwer rejestruje się, wpisów, które umieszcza je w bazie danych rejestracji systemu (Registry) opisano każdy typ obiektu, który dostarcza mu, plik rozszerzenia, a ścieżka do samego siebie, między innymi informacjami.

Struktura i bibliotek DLL systemu OLE (DLL) za pomocą tego rejestru do określenia, jakie typy elementów OLE są dostępne w systemie. OLE system biblioteki DLL również za pomocą tego rejestru do określenia sposobu uruchamiania aplikacji serwera, po aktywowaniu obiekt osadzony lub połączony.

W tym artykule opisano, co trzeba zrobić, gdy jest zainstalowany każdej aplikacji serwera i zawsze jest wykonywane.

Aby uzyskać szczegółowe informacje o systemowej bazy danych rejestracji i format plików reg, używane do aktualizowania go, zobacz *OLE Podręcznik programisty*.

##  <a name="_core_server_installation"></a> Instalacja serwera

Podczas pierwszej instalacji aplikacji serwera, wymagana jest rejestracja wszystkich typów elementów OLE, które obsługuje. Mogą też istnieć serwer aktualizacji systemowej bazy danych rejestracji, za każdym razem, gdy jest wykonywany jako autonomiczną aplikację. Dzięki temu baza danych rejestracji aktualne przypadku przeniesienia pliku wykonywalnego serwera.

> [!NOTE]
>  Aplikacje MFC automatycznie generowane przez Kreatora aplikacji rejestrują się, gdy są uruchamiane jako autonomiczne aplikacje.

Jeśli chcesz zarejestrować swoją aplikację, podczas instalacji, należy użyć programu RegEdit.exe. Jeśli dołączysz program instalacyjny z aplikacją ma uruchomić program instalacyjny "RegEdit /S *appname*reg". (Flaga /S wskazuje operację w trybie dyskretnym, oznacza to, że nie są wyświetlane okno dialogowe raportowania pomyślne wykonanie polecenia). W przeciwnym razie Poinstruuj użytkownika, aby ręcznie uruchomić program RegEdit.

> [!NOTE]
>  Plik reg, tworzone przez Kreatora aplikacji nie zawiera pełną ścieżkę dla pliku wykonywalnego. Program instalacyjny albo zmodyfikować plik reg, które obejmują pełną ścieżkę do pliku wykonywalnego lub zmodyfikować zmienną środowiskową PATH, aby uwzględnić w katalogu instalacyjnym.

RegEdit Scala zawartość pliku tekstowego reg baza danych rejestracji. Aby weryfikować bazę danych lub napraw go, użyj Edytora rejestru. Należy zadbać, aby uniknąć usunięcia niezbędne wpisy OLE.

##  <a name="_core_server_initialization"></a> Inicjowanie serwera

Po utworzeniu aplikacji serwera za pomocą Kreatora aplikacji, Kreator zakończy pracę wszystkich zadań inicjowania dla Ciebie automatycznie. W tej sekcji opisano, co należy zrobić, jeśli ręcznie napisać aplikację serwera.

Po uruchomieniu aplikacji serwera przez aplikację kontenera OLE systemowych bibliotek DLL należy dodać opcję "/ osadzania" do wiersza polecenia serwera. Zachowanie aplikacji serwera, który różni się w zależności od tego, czy jej uruchamiania przez kontener, więc pierwszą rzeczą, aplikacja powinna wykonać, gdy rozpocznie się wykonywanie sprawdzania dla "/ osadzania" lub "-osadzania" opcji w wierszu polecenia. Jeśli istnieje tego przełącznika, załadować zestaw zasobów, które pokazują server jako znajdujące się albo aktywny w miejscu lub pełni Otwórz. Aby uzyskać więcej informacji, zobacz [menu i zasoby: dodatki do serwera](../mfc/menus-and-resources-server-additions.md).

Aplikacja serwera powinien także wywołać jej `CWinApp::RunEmbedded` funkcję do analizowania wiersza polecenia. Jeśli zwraca wartość różną od zera, aplikacja nie powinna wyświetlone okno, ponieważ została uruchomiona z aplikacji kontenera, nie jako autonomiczną aplikację. Ta funkcja aktualizuje wpis serwera bazy danych rejestracji systemu i wywołania `RegisterAll` funkcja elementu członkowskiego dla Ciebie wykonywania wystąpienia rejestracji.

Przy uruchamianiu aplikacji serwera należy się upewnić, że można wykonywać rejestracji wystąpienia. Wystąpienie rejestracji informuje OLE systemowych bibliotek DLL, że serwer jest aktywne i gotowe do odbierania żądań z kontenerów. Nie dodaje wpis w bazie danych rejestracji. Przeprowadzenia rejestracji wystąpienia serwera, wywołując `ConnectTemplate` funkcja elementu członkowskiego zdefiniowane przez `COleTemplateServer`. Łączy to `CDocTemplate` obiekt `COleTemplateServer` obiektu.

`ConnectTemplate` Funkcja przyjmuje trzy parametry: serwera *CLSID*, wskaźnik do `CDocTemplate` obiektu i flagę wskazującą, czy serwer obsługuje wiele wystąpień. Miniserver musi mieć możliwość zapewnienia obsługi wielu wystąpień, oznacza to, musi być możliwe dla wielu wystąpień serwera ma być uruchomione jednocześnie, jeden dla każdego kontenera. W związku z tym, przekazać **TRUE** tej flagi, podczas uruchamiania miniserver.

Jeśli piszesz miniserver, zgodnie z definicją, który zostanie uruchomiony zawsze przez kontener. Nadal należy przeanalizować wiersza polecenia, aby sprawdzić, czy opcja "/ osadzania". Braku tej opcji w wierszu polecenia oznacza, że użytkownik ma próbowano uruchomić miniserver jako autonomiczną aplikację. W takiej sytuacji należy zarejestrować serwer przy użyciu systemowej bazy danych rejestracji, a następnie wyświetlić okno komunikatu, informujący użytkownika, aby uruchomić miniserver z aplikacji kontenera.

## <a name="see-also"></a>Zobacz też

[OLE](../mfc/ole-in-mfc.md)<br/>
[Serwery](../mfc/servers.md)<br/>
[CWinApp::RunAutomated](../mfc/reference/cwinapp-class.md#runautomated)<br/>
[CWinApp::RunEmbedded](../mfc/reference/cwinapp-class.md#runembedded)<br/>
[Klasa COleTemplateServer](../mfc/reference/coletemplateserver-class.md)
