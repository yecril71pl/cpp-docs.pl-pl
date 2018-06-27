---
title: Uaktualnianie istniejącego formantu ActiveX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [MFC], Internet
- LPK files for Internet controls
- safe for scripting and initialization (controls)
- OLE controls [MFC], upgrading to ActiveX
- CAB files, for ActiveX controls
- Internet applications [MFC], ActiveX controls
- Internet applications [MFC], packaging code for download
- upgrading ActiveX controls
- licensing ActiveX controls
ms.assetid: 4d12ddfa-b491-4f9f-a0b7-b51458e05651
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 145546a83bb91d09499049308b8d37e5adafeb92
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955677"
---
# <a name="upgrading-an-existing-activex-control"></a>Uaktualnianie istniejącego kontrolki ActiveX
Formanty ActiveX istniejących (dawniej formanty OLE) można używać w Internecie bez żadnych modyfikacji. Można zmodyfikować formantów, aby zwiększyć ich wydajność. Korzystając z formantu na stronie sieci Web, istnieją dodatkowe zagadnienia. Plik ocx i wszystkie pliki pomocnicze musi znajdować się na komputerze docelowym lub można pobrać przez Internet. Dzięki temu rozmiar kodu i pobierania czasu ważną kwestią. W pliku cab podpisem można spakować pliki do pobrania. Można oznaczyć jako bezpieczne do wykonywania skryptów i jako bezpieczne inicjowanie formantu.  
  
 W tym artykule omówiono następujące zagadnienia:  
  
- [Kod opakowania do pobrania](#_core_packaging_code_for_downloading)  
  
- [Oznaczenie bezpieczne kontrolki dla wykonywania skryptów i inicjalizacji](#_core_marking_a_control_safe_for_scripting_and_initializing)  
  
- [Licencjonowania](#_core_licensing_issues)  
  
- [Podpisywanie kodu](#_core_signing_code)  
  
- [Zarządzanie palety](#_core_managing_the_palette)  
  
- [Programu Internet Explorer przeglądarki poziom bezpieczeństwa i kontroli zachowania](#_core_internet_explorer_browser_safety_levels_and_control_behavior)  
  
 Możesz także dodać optymalizacje, zgodnie z opisem w [formantów ActiveX: Optymalizacja](../mfc/mfc-activex-controls-optimization.md). Monikery może służyć do pobierania właściwości i dużych obiektów blob asynchronicznie, zgodnie z opisem w [formantów ActiveX w Internecie](../mfc/activex-controls-on-the-internet.md).  
  
##  <a name="_core_packaging_code_for_downloading"></a> Kod opakowania do pobrania  
 Aby uzyskać więcej informacji na ten temat zobacz artykuł bazy wiedzy Knowledge Base "Opakowania MFC formantów dla Użyj za pośrednictwem Internetu" (Q167158). Można znaleźć artykuły bazy wiedzy w [ http://support.microsoft.com/support ](http://support.microsoft.com/support).  
  
### <a name="the-codebase-tag"></a>CODEBASE Tag  
 Formanty ActiveX są osadzone na stronach sieci Web przy użyciu `<OBJECT>` tagu. `CODEBASE` Parametr `<OBJECT>` tag Określa lokalizację, z której można pobrać formantu. `CODEBASE` można wskazać pomyślnie na wielu różnych typów plików.  
  
### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Przy użyciu CODEBASE Tag przy użyciu pliku OCX  
  
```  
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"  
```  
  
 To rozwiązanie pobiera tylko plik ocx formantu i wymaga już być zainstalowany na komputerze klienta biblioteki obsługi dll. To będzie działać dla programu Internet Explorer i MFC formantów ActiveX skompilowanej za pomocą programu Visual C++, ponieważ program Internet Explorer jest dostarczany z pomocniczych biblioteki DLL dla formantów Visual C++. Jeśli innej przeglądarki internetowej, będącą funkcją formantu ActiveX służy do wyświetlania tego formantu, to rozwiązanie nie będzie działać.  
  
### <a name="using-the-codebase-tag-with-an-inf-file"></a>Korzystanie z pliku INF CODEBASE Tag  
  
```  
CODEBASE="http://example.microsoft.com/trustme.inf"  
```  
  
 Plik .inf kontroli instalacji .ocx i jego pliki pomocnicze. Ta metoda nie jest zalecane, ponieważ nie jest możliwe do podpisywania pliku .inf (zobacz [podpisywania kodu](#_core_signing_code) dla wskaźników na podpisywanie kodu).  
  
### <a name="using-the-codebase-tag-with-a-cab-file"></a>Używanie CODEBASE Tag z pliku CAB  
  
```  
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"  
```  
  
 Pliki cab są zalecanym sposobem formantów ActiveX pakietu, które używają MFC. Kontrolki MFC ActiveX w pliku cabinet pakowania umożliwia pliku .inf do uwzględnienia kontroli Instalacja formantu ActiveX i wszelkich zależnych bibliotek DLL (takich jak biblioteki DLL MFC). Przy użyciu pliku CAB automatycznie kompresuje kod szybsze pobieranie. Korzystania z pliku cab do pobrania składnika jest szybsze do podpisywania pliku cab całego niż poszczególnych składników.  
  
### <a name="creating-cab-files"></a>Tworzenie plików CAB  
 Plik Cabinet Development Kit można pobrać z artykułu bazy wiedzy [310618: Microsoft Cabinet Software Development Kit](http://go.microsoft.com/fwlink/p/?linkid=148204). Ten zestaw zawiera narzędzia niezbędne do utworzenia plików cabinet.  
  
 Plik cabinet wskazywana przez `CODEBASE` powinien zawierać plik ocx dla formantu ActiveX i pliku .inf, aby kontrolować jego instalacji. Tworzy plik cab, określając nazwę pliku kontroli i plik inf. Nie dołączaj zależnych bibliotek DLL, które może już istnieć w systemie, w tym pliku cabinet. Na przykład biblioteki DLL MFC są umieszczone w osobnym pliku cabinet i odwołuje się plik .inf kontrolowanie.  
  
 Aby uzyskać szczegółowe informacje dotyczące sposobu tworzenia pliku CAB, zobacz [tworzenia pliku CAB](http://msdn.microsoft.com/en-us/cc52fd09-bdf6-4410-a693-149a308f36a3).  
  
### <a name="the-inf-file"></a>Plik INF  
 Poniższy przykład, spindial.inf, listy plików pomocniczych i informacje o wersji potrzebne w przypadku MFC Spindial kontroli. Należy zauważyć, że lokalizacja biblioteki DLL MFC jest witryną sieci Web firmy Microsoft. Mfc42.cab ma być dostarczana i podpisane przez firmę Microsoft.  
  
```  
Contents of spindial.inf:  
[mfc42installer]   
file-win32-x86=http://activex.microsoft.com/controls/vc/mfc42.cab   
[Olepro32.dll] - FileVersion=5,
    0,
    4261,
    0  
[Mfc42.dll] - FileVersion=6,
    0,
    8168,
    0  
[Msvcrt.dll] - FileVersion=6,
    0,
    8168,
    0  
```  
  
### <a name="the-object-tag"></a>\<Obiektu > Tag  
 Poniższy przykład przedstawia przy użyciu `<OBJECT>` tag do pakietu kontroli próbki MFC Spindial.  
  
```  
<OBJECT ID="Spindial1" WIDTH=100 HEIGHT=51  
    CLASSID="CLSID:06889605-B8D0-101A-91F1-00608CEAD5B3" 
    CODEBASE="http://example.microsoft.com/spindial.cab#Version=1,0,0,001"> 
 <PARAM NAME="_Version" VALUE="65536">  
 <PARAM NAME="_ExtentX" VALUE="2646">  
 <PARAM NAME="_ExtentY" VALUE="1323">  
 <PARAM NAME="_StockProps" VALUE="0">  
 <PARAM NAME="NeedlePosition" VALUE="2">  
</OBJECT>  
```  
  
 W takim przypadku spindial.cab będzie zawierać dwa pliki, spindial.ocx i spindial.inf. Następujące polecenie spowoduje kompilacji pliku cabinet:  
  
```  
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf   
```  
  
 `-s 6144` Parametr rezerwuje miejsce w pliku cab do podpisywania kodu.  
  
### <a name="the-version-tag"></a>Tag wersji  
 Tutaj zauważyć, że `#Version` informacji z pliku CAB ma zastosowanie do określonego przez formant *CLASSID* parametr `<OBJECT>` tagu.  
  
 W zależności od wersji określone możesz wymusić pobierania formantu. Do ukończenia specyfikacji `OBJECT` tym tag *CODEBASE* parametrów, zobacz W3C odwołania.  
  
##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a> Oznaczenie bezpieczne kontrolki dla wykonywania skryptów i inicjalizacji  
 Kontrolki ActiveX używana na stronach sieci Web powinien być oznaczony jako bezpieczne do wykonywania skryptów i bezpieczne inicjowanie, jeśli w rzeczywistości są bezpieczne. Bezpieczne kontrolki zostanie nie we/wy dysku lub wykonać bezpośrednio uzyskać dostęp do pamięci lub rejestrów maszyny.  
  
 Formanty może być oznaczony jako bezpieczne do wykonywania skryptów i bezpieczne inicjowanie za pomocą rejestru. Modyfikowanie `DllRegisterServer` można dodać pozycje podobne do następujących czynności, aby oznaczyć formant jako bezpieczne do wykonywania skryptów i trwałości w rejestrze. Alternatywną metodą jest zaimplementowanie `IObjectSafety`.  
  
 Identyfikatory GUID (globalnie unikatowych identyfikatorów) zostaną zdefiniowane dla formantu w taki sposób oznaczyć go jako bezpieczne do wykonywania skryptów i trwałości. Formanty, które można bezpiecznie uwzględnione w skryptach będzie zawierać wpisu rejestru podobny do następującego:  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 Formanty, które można bezpiecznie zainicjować z trwałych danych są oznaczone bezpieczne trwałości z podobne do wpisu rejestru:  
  
```  
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}  
```  
  
 Dodaj wpisy podobne do następujących (zastępując formantu identyfikator zamiast klasy `{06889605-B8D0-101A-91F1-00608CEAD5B3}`) do skojarzenia z następującym Identyfikatorem klasy kluczy:  
  
```  
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}   
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}   
```  
  
##  <a name="_core_licensing_issues"></a> Licencjonowania  
 Jeśli chcesz użyć licencjonowanego formantu na stronie sieci Web, należy sprawdzić, czy umowa licencyjna umożliwia jego użyciem w Internecie i utworzenie pliku pakietu licencji (LPK) dla niego.  
  
 Licencjonowanego formantu ActiveX nie zostanie załadowany prawidłowo na stronie HTML w przypadku komputera z uruchomionym programu Internet Explorer nie ma licencji na korzystanie z kontroli. Na przykład jeśli licencjonowanego formantu został utworzony przy użyciu programu Visual C++, strony HTML przy użyciu formantu zostanie załadowany prawidłowo na komputerze, gdy formant został utworzony, ale go nie zostanie załadowany na innym komputerze, chyba że wśród nich informacji licencjonowania.  
  
 Aby użyć licencjonowanego formantu ActiveX w programie Internet Explorer, należy sprawdzić umowy licencyjnej dostawcy, aby sprawdzić, czy zezwala na licencji dla formantu:  
  
-   Redystrybucja  
  
-   Użyj formantu w Internecie  
  
-   Użycie parametru Codebase  
  
 Aby użyć licencjonowanego formantu na stronie HTML na maszynie nonlicensed, należy wygenerować pliku pakietu licencji (LPK). Plik LPK zawiera licencji czasu wykonywania dla licencjonowane formanty na stronie HTML. Ten plik został wygenerowany za pomocą LPK_TOOL. EXE, który jest dostarczany z zestawem SDK ActiveX. Aby uzyskać więcej informacji, zobacz witrynę sieci Web MSDN pod [ http://msdn.microsoft.com ](http://msdn.microsoft.com).  
  
#### <a name="to-create-an-lpk-file"></a>Aby utworzyć plik LPK  
  
1.  Uruchom LPK_TOOL. EXE na komputerze, który jest licencji na korzystanie z formantu.  
  
2.  W **narzędzia autorskiego pakietu licencji** okna dialogowego, **dostępnych formantów** pola listy, wybierz wszystkie licencjonowane formantu ActiveX, który będzie używany na stronie HTML i kliknij przycisk **Dodaj**.  
  
3.  Kliknij przycisk **Zapisz i Zamknij** i wpisz nazwę pliku LPK. Spowoduje to utworzenie pliku LPK i zamknij aplikację.  
  
#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Aby osadzić licencjonowanego formantu na stronie HTML  
  
1.  Edytuj stronę HTML. Na stronie HTML wstawić \<obiektu > tag dla obiekt License Manager przed wszystkimi innymi \<obiektu > tagów. Menedżer licencji jest formantu ActiveX, który jest instalowany z programu Internet Explorer. Poniżej przedstawiono jego identyfikator klasy. Ustaw właściwość LPKPath obiektu License Manager, ścieżka i nazwa pliku LPK. Może mieć tylko jeden plik LPK na stronie HTML.  
  
 ```  
 <OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
 <PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">  
 </OBJECT>  
 ```  
  
2.  Wstaw \<obiektu > tag licencjonowanego formantu po znaczniku Menedżer licencji.  
  
     Na przykład strona HTML, która wyświetla kontrolka zamaskowanej edycji Microsoft przedstawiono poniżej. Pierwszy klasy, która jest identyfikator formantu License Manager, drugiej klasy, którego identyfikator kontrolka zamaskowanej edycji. Zmień znaczniki, aby wskazać ścieżkę względną wcześniej utworzony plik lpk i dodać tag object w tym identyfikator klasy formantu.  
  
3.  Wstaw \<osadzania > atrybutu pliku LPK, jeśli przy użyciu wtyczki NCompass ActiveX.  
  
     Jeśli formantu mogą być wyświetlane w drugiej aktywny włączone przeglądarek — na przykład Netscape przy użyciu wtyczki NCompass ActiveX — należy dodać \<osadzania > składni, jak pokazano poniżej.  
  
 ```  
 <OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">  
 <PARAM NAME="LPKPath" VALUE="maskedit.lpk">  
 
 <EMBED SRC = "maskedit.LPK">  
 
 </OBJECT>  
 <OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>  
 </OBJECT>  
 ```  
  
 Aby uzyskać więcej informacji na temat licencjonowania kontroli, zobacz [formantów ActiveX: Licencjonowanie formantu ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md).  
  
##  <a name="_core_signing_code"></a> Podpisywanie kodu  
 Podpisywanie kodu zaprojektowano w celu zidentyfikowania źródła kodu, a aby zagwarantować, że kod nie zmienił się od jej została podpisana. W zależności od ustawienia bezpieczeństwa przeglądarki użytkownicy mogą otrzymywać ostrzeżenie przed pobraniem kodu. Użytkownicy mogą wybrać opcję zaufania określonych właścicieli certyfikatu lub przedsiębiorstwa, w których wielkość kod jest podpisywany przez osoby zaufane, zostaną pobrane bez ostrzeżenia. Kod jest podpisany cyfrowo, aby zapobiec naruszeniu.  
  
 Upewnij się, że końcowego kodu jest podpisany, dzięki czemu formantu można automatycznie pobrać bez wyświetlania ostrzeżeń zaufania. Aby uzyskać więcej informacji na temat podpisywania kodu, zapoznaj się z dokumentacją na Authenticode w zestawie SDK ActiveX i zobacz [podpisywania pliku CAB](http://msdn.microsoft.com/en-us/04d8b47a-8f1c-4b54-ab90-730fcdc03747).  
  
 W zależności od zaufania i przeglądarki poziomu ustawienia bezpieczeństwa certyfikat może być wyświetlany do identyfikowania osoby lub firmy podpisywania. Jeśli poziom bezpieczeństwa nie none lub właściciela certyfikatu z podpisem formantu jest zaufany, certyfikat nie będą wyświetlane. Zobacz [programu Internet Explorer przeglądarki poziom bezpieczeństwa i kontroli zachowania](#_core_internet_explorer_browser_safety_levels_and_control_behavior) szczegółowe informacje na temat jak ustawienie bezpieczeństwa przeglądarki określi, czy formant jest pobierany i wyświetlane certyfikatu.  
  
 Cyfrowego podpisywania kodu gwarancje nie została zmieniona, ponieważ jest on podpisany. Skrót kodu jest poświęcony i osadzone w certyfikacie. Ten skrót później jest porównywany ze skrótu podejmowane po pobraniu kod, ale przed uruchomieniem kodu. Firm, takich jak Verisign, można podać kluczy prywatnych i publicznych, niezbędnych do podpisywania kodu. Zestaw SDK ActiveX jest dostarczany z MakeCert, narzędzie do tworzenia certyfikatów testu.  
  
##  <a name="_core_managing_the_palette"></a> Zarządzanie palety  
 Kontenery określić paletę i udostępni go jako właściwością otoczenia **DISPID_AMBIENT_PALETTE**. Kontener (na przykład Internet Explorer) wybiera paletę jest używany przez wszystkie kontrolki ActiveX na stronie w celu określenia własnych palety. Uniemożliwia wyświetlanie migotanie i przedstawia spójny wygląd.  
  
 Można zastąpić formantu `OnAmbientPropertyChange` do obsługi powiadomień o zmianach palety.  
  
 Można zastąpić formantu `OnGetColorSet` do zwrócenia zestaw do rysowania paletę kolorów. Kontenery, użyj wartości zwracanej do ustalenia, czy formant jest obsługujący palety.  
  
 W obszarze wytyczne OCX 96 formant zawsze należy pamiętać swoją paletę w tle.  
  
 Starsze kontenerów, które nie korzystają z właściwością otoczenia palety wyśle WM_QUERYNEWPALETTE i WM_PALETTECHANGED wiadomości. Można zastąpić formantu `OnQueryNewPalette` i `OnPaletteChanged` do obsługi tych wiadomości.  
  
##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a> Programu Internet Explorer przeglądarki poziom bezpieczeństwa i kontroli zachowania  
 Przeglądarka musi opcje poziom bezpieczeństwa, można skonfigurować przez użytkownika. Strony sieci Web może zawierać zawartość, która może być szkodliwe dla komputera użytkownika, przeglądarek Zezwalaj użytkownikowi na wybranie opcji poziom bezpieczeństwa. W zależności od sposobu, w przeglądarce implementuje poziom bezpieczeństwa formantu nie może zostać pobrana w ogóle lub wyświetli certyfikatu lub komunikat ostrzegawczy, aby zezwolić użytkownikowi na wybranie w czasie wykonywania, czy nie można pobrać formantu. Poniżej przedstawiono zachowania formantów ActiveX w obszarze poziom bezpieczeństwa wysoki, średni i niski w programie Internet Explorer.  
  
### <a name="high-safety-mode"></a>Tryb wysokiego bezpieczeństwa  
  
-   Nie będzie można pobrać formantów bez znaku.  
  
-   Podpisane formanty wyświetli certyfikatu, jeśli niezaufany (użytkownik może wybrać opcję, aby zawsze ufaj kod z tego właściciela certyfikatu od teraz).  
  
-   Tylko formanty oznaczone jako bezpieczne będzie mieć trwałych danych i/lub być skryptowe.  
  
### <a name="medium-safety-mode"></a>Tryb bezpieczeństwa średnia  
  
-   Niepodpisane formanty wyświetli ostrzeżenie przed pobraniem.  
  
-   Jeśli niezaufany podpisane formanty wyświetli certyfikatu.  
  
-   Formanty nie jest oznaczony jako bezpieczny zostanie wyświetlone ostrzeżenie.  
  
### <a name="low-safety-mode"></a>Tryb niski poziom zabezpieczeń  
  
-   Formanty są pobierane bez ostrzeżenia.  
  
-   Obsługa skryptów i trwałości odbywa się bez ostrzeżenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania związane z programowaniem Internetu MFC](../mfc/mfc-internet-programming-tasks.md)   
 [MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)   
 [Kontrolki ActiveX MFC: licencjonowanie kontrolki ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)

