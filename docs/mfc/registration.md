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
ms.openlocfilehash: 6d51589d9261d497c4c1f9185bd90b889e46eb34
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930693"
---
# <a name="registration"></a>Rejestracja
Gdy użytkownik chce, aby wstawić element OLE do aplikacji, OLE wyświetla listę typów obiektów do wyboru. OLE pobiera tej listy z systemu bazie danych rejestracji, który zawiera informacje o wszystkich aplikacji serwera. Gdy serwer rejestruje się, wpisów, które następnie są umieszczane w bazie danych rejestracji systemu (rejestr) opis każdego typu obiektu, który dostarcza mu, rozszerzenia i ścieżki do samej siebie, między innymi informacje o pliku.  
  
 Platformę i OLE systemu dołączanych dynamicznie bibliotekach (DLL) używają tego rejestru w celu określenia, jakie typy elementów OLE są dostępne w systemie. OLE system biblioteki DLL również używać tego rejestru do określenia sposobu uruchamiania aplikacji serwera, po aktywowaniu połączonego lub osadzonego obiektu.  
  
 W tym artykule opisano, każda aplikacja serwera wymaga robić, jeśli jest zainstalowana i zawsze jest wykonywana.  
  
 Aby uzyskać szczegółowe informacje o bazie danych rejestracji systemu oraz format plików reg używane do aktualizowania go, zobacz *OLE Podręcznik programisty*.  
  
##  <a name="_core_server_installation"></a> Instalacja serwera  
 Po zainstalowaniu aplikacji serwera, należy go zarejestrować wszystkich typów elementów OLE, które obsługuje. Może także zawierać serwera aktualizacji bazy danych rejestracji systemu, za każdym razem, gdy jest wykonywany jako aplikacja autonomiczna. Dzięki temu bazy danych rejestracji aktualne przypadku przeniesienia pliku wykonywalnego serwera.  
  
> [!NOTE]
>  Aplikacje MFC automatycznie generowane przez Kreatora aplikacji rejestrują się uruchomienie jako aplikacji autonomicznych.  
  
 Jeśli chcesz zarejestrować aplikację podczas instalacji, należy użyć programu RegEdit.exe. Jeśli program instalacyjny z aplikacją, uruchom program instalacyjny ma "RegEdit /S *appname*reg". (Flaga /S wskazuje operację w trybie dyskretnym, oznacza to, że nie są wyświetlane okno dialogowe raportowania pomyślne zakończenie polecenia). W przeciwnym razie Poinstruuj użytkowników, aby ręcznie uruchomić program RegEdit.  
  
> [!NOTE]
>  Plik reg utworzonego przez Kreatora aplikacji nie zawiera pełną ścieżkę do pliku wykonywalnego. Program instalacyjny albo zmodyfikować pliku reg zawierać pełną ścieżkę do pliku wykonywalnego lub zmodyfikować zmiennej środowiskowej PATH, aby uwzględnić katalogu instalacyjnego.  
  
 RegEdit Scala zawartość pliku tekstowego reg w bazie danych rejestracji. Aby sprawdzić bazy danych lub w celu jego naprawy Edytor rejestru. Należy zadbać, aby uniknąć usunięcia niezbędne zapisów OLE.  
  
##  <a name="_core_server_initialization"></a> Inicjowanie serwera  
 Po utworzeniu aplikacji serwera za pomocą Kreatora aplikacji, Kreator zakończy pracę wszystkich zadań inicjowania dla Ciebie automatycznie. W tej sekcji opisano, co należy zrobić ręcznie podczas pisania aplikacji serwera.  
  
 Gdy aplikacja serwera jest uruchamiana przez aplikacji kontenera, OLE systemowej biblioteki DLL dodać opcji "/ osadzania" do wiersza polecenia serwera. Aplikacja serwera zachowanie różni się w zależności od tego, czy została ona uruchomiona przez kontener, dlatego najpierw aplikacja powinna wykonać po jej rozpoczęciu wykonywania Sprawdź, czy "/ osadzania" lub "-Embedding" opcji w wierszu polecenia. Jeśli istnieje ten przełącznik, Załaduj zestaw zasobów, które Pokaż serwera jako albo aktywny w miejscu lub pełni otworzyć. Aby uzyskać więcej informacji, zobacz [menu i zasoby: dodatki do serwera](../mfc/menus-and-resources-server-additions.md).  
  
 Aplikacja serwera należy także wywołać jej `CWinApp::RunEmbedded` funkcji, aby przeanalizować wiersza polecenia. Jeśli zmienna zwraca wartość niezerową, aplikacji nie powinna pokazać okna, ponieważ została uruchomiona z poziomu aplikacji kontenera, nie jako aplikacja autonomiczna. Ta funkcja aktualizuje wpis serwera bazy danych rejestracji systemu i wywołania `RegisterAll` funkcji członkowskiej dla Ciebie wykonywania wystąpienia rejestracji.  
  
 Przy uruchamianiu aplikacji serwera należy się upewnić, czy można wykonać rejestracja wystąpienia. Rejestracja wystąpienia informuje o OLE systemowej biblioteki dll, że serwer jest aktywne i gotowe do odbierania żądań z kontenerów. Nie dodaje wpis w bazie danych rejestracji. Dokonać rejestracji wystąpienia serwera, wywołując `ConnectTemplate` funkcji członkowskich zdefiniowanych przez `COleTemplateServer`. Utworzone połączenie `CDocTemplate` do obiektu `COleTemplateServer` obiektu.  
  
 `ConnectTemplate` Funkcja przyjmuje trzy parametry: serwera *CLSID*, wskaźnik do `CDocTemplate` obiekt i flagę wskazującą, czy serwer obsługuje wiele wystąpień. Miniserver musi mieć możliwość obsługi wielu wystąpień, oznacza to, musi być możliwe w dla wielu wystąpień serwera, aby działać jednocześnie, po jednej dla każdego kontenera. W rezultacie przekazać **TRUE** tej flagi przy uruchamianiu miniserver.  
  
 Jeśli piszesz miniserver zgodnie z definicją go będzie zawsze uruchamiana przez kontener. Nadal należy przeanalizować wiersza polecenia, aby sprawdzić, czy opcja "/ osadzania". Brak tej opcji w wierszu polecenia oznacza, że użytkownik próbował uruchomić miniserver jako aplikacja autonomiczna. W takim przypadku rejestracja serwera w usłudze baza danych rejestracji systemu, a następnie Wyświetl okno komunikatu informujące użytkownika, aby uruchomić miniserver z kontenera aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [OLE](../mfc/ole-in-mfc.md)   
 [Serwery](../mfc/servers.md)   
 [CWinApp::RunAutomated](../mfc/reference/cwinapp-class.md#runautomated)   
 [CWinApp::RunEmbedded](../mfc/reference/cwinapp-class.md#runembedded)   
 [Klasa COleTemplateServer](../mfc/reference/coletemplateserver-class.md)
