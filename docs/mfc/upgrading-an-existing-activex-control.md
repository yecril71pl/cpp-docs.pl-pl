---
title: Uaktualnianie istniejącego kontrolki ActiveX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2018
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
ms.openlocfilehash: 2ddf4b505689521fbdfd702eb1944ac0779f16bf
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409574"
---
# <a name="upgrading-an-existing-activex-control"></a>Uaktualnianie istniejącego kontrolki ActiveX

Kontrolki ActiveX istniejących (dawniej kontrolka OLE) może służyć w Internecie bez żadnych modyfikacji. Można zmodyfikować formantów, aby zwiększyć ich wydajność.

> [!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które wypierają ActiveX zobacz [formantów ActiveX](activex-controls.md).

Korzystając z kontrolki na stronie sieci Web, istnieją dodatkowe zagadnienia. Plik ocx i wszystkie pliki obsługi muszą znajdować się na komputerze docelowym lub można pobrać przez Internet. To sprawia, że rozmiar kodu i pobierania czasu ważną kwestią. W pliku .cab podpisanych można spakować pliki do pobrania. Możesz oznaczyć obsługi skryptów, jak i bezpiecznie zainicjować formant.

W tym artykule omówiono następujące tematy:

- [Kod opakowania do pobrania](#_core_packaging_code_for_downloading)

- [Oznaczanie bezpiecznej kontrolki do wykonywania skryptów i inicjalizacji](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [Problemy z licencjonowaniem](#_core_licensing_issues)

- [Podpisywanie kodu](#_core_signing_code)

- [Zarządzanie palety](#_core_managing_the_palette)

- [Internet Explorer przeglądarki bezpieczeństwa poziomy i zachowanie kontroli](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

Możesz również dodać optymalizacje, zgodnie z opisem w [kontrolek ActiveX: Optymalizacja](../mfc/mfc-activex-controls-optimization.md). Monikery może służyć do pobierania właściwości i duże obiekty BLOB asynchronicznie, zgodnie z opisem w [kontrolki ActiveX w Internecie](../mfc/activex-controls-on-the-internet.md).

##  <a name="_core_packaging_code_for_downloading"></a> Kod opakowania do pobrania

Aby uzyskać więcej informacji na ten temat zobacz artykuł bazy wiedzy Knowledge Base "Pakowania MFC formantów dla użycia nad Internetem" (Q167158). Możesz znaleźć artykuły bazy wiedzy w [ http://support.microsoft.com/support ](http://support.microsoft.com/support).

### <a name="the-codebase-tag"></a>Tag kodu

Kontrolki ActiveX są osadzone w stronach sieci Web przy użyciu `<OBJECT>` tagu. `CODEBASE` Parametru `<OBJECT>` tag Określa lokalizację, z którego będą pobierane kontrolki. `CODEBASE` można wskazać pomyślnie na wielu różnych typów plików.

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Przy użyciu tagu bazy kodu z plikiem OCX

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

To rozwiązanie pobiera tylko plik .ocx formantu i wymaga wszystkie pomocnicze bibliotek DLL w celu już być zainstalowany na komputerze klienckim. To będzie działać w przypadku programu Internet Explorer i MFC formantów ActiveX utworzonych za pomocą języka Visual C++, ponieważ program Internet Explorer jest dostarczany z obsługi bibliotek DLL dla kontrolek Visual C++. Jeśli innej przeglądarki internetowej, który jest zdolny do kontrolki ActiveX jest używany do wyświetlania tej kontrolki, to rozwiązanie nie będzie działać.

### <a name="using-the-codebase-tag-with-an-inf-file"></a>Przy użyciu tagu CODEBASE przy użyciu pliku INF

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

Plik inf będzie kontrolować instalację .ocx i jego pliki pomocnicze. Ta metoda nie jest zalecane, ponieważ nie jest możliwe do podpisania pliku .inf (zobacz [podpisywania kodu](#_core_signing_code) dla wskaźników na podpisywanie kodu).

### <a name="using-the-codebase-tag-with-a-cab-file"></a>Przy użyciu tagu bazy kodu z pliku CAB

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

Pliki cabinet są zalecanym sposobem formantów ActiveX pakietów korzystających z biblioteki MFC. Pakowanie kontrolki MFC ActiveX w pliku cabinet umożliwia plik inf dołączonych do sterowania instalacji formant ActiveX i wszelkie zależne biblioteki dll (np. biblioteki MFC dll). Przy użyciu pliku CAB automatycznie kompresuje kod szybciej pobierania. Jeśli używasz pliku cab do pobrania składnik, jest szybsze do podpisania pliku cab całego niż każdego składnika.

### <a name="creating-cab-files"></a>Tworzenie plików CAB

Plik Cabinet Development Kit można pobrać z artykułu bazy wiedzy [310618: Microsoft pliku Cabinet Software Development Kit](http://go.microsoft.com/fwlink/p/?linkid=148204). Ten zestaw zawiera narzędzia niezbędne do utworzenia plików cabinet.

Plik cabinet wskazywany przez `CODEBASE` powinien zawierać plik ocx kontrolki ActiveX i pliku .inf, aby kontrolować jego instalacji. Tworzenie pliku cabinet, określając nazwę pliku kontroli i plik inf. Nie dołączaj zależne biblioteki dll, które mogą już istnieć w systemie, w tym pliku cabinet. Na przykład biblioteki MFC DLL są spakowane w oddzielnym pliku cabinet i kontrolowanie pliku inf.

Aby uzyskać więcej informacji na temat tworzenia pliku CAB, zobacz [tworzenia pliku CAB](/windows/desktop/devnotes/cabinet-api-functions).

### <a name="the-inf-file"></a>Plik INF

Poniższy przykład, spindial.inf, listy plików oraz informacje o wersji wymagane w przypadku MFC Spindial kontroli. Należy zauważyć, że lokalizacja biblioteki MFC dll to witrynie internetowej firmy Microsoft. Mfc42.cab ma być dostarczana i podpisany przez firmę Microsoft.

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

Poniższy przykład ilustruje użycie `<OBJECT>` tag do sterowania próbki MFC Spindial pakietu.

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

W tym przypadku spindial.cab będzie zawierać dwa pliki, spindial.ocx i spindial.inf. Poniższe polecenie utworzy plik cabinet:

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

`-s 6144` Parametr rezerwuje miejsce w pliku cab do podpisywania kodu.

### <a name="the-version-tag"></a>Tag wersji

Tutaj zauważyć, że `#Version` informacji określony za pomocą pliku CAB, który ma zastosowanie do kontrolki określonej przez *CLASSID* parametru `<OBJECT>` tagu.

W zależności od wersji określonej możesz wymusić pobierania formantu. Aby uzyskać pełną specyfikacji `OBJECT` tagu w tym *CODEBASE* parametrów, zobacz W3C odwołania.

##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a> Oznaczanie bezpiecznej kontrolki do wykonywania skryptów i inicjalizacji

Kontrolki ActiveX używane na stronach sieci Web powinien być oznaczony jako bezpieczne do wykonywania i bezpiecznie zainicjować w przypadku w rzeczywistości są one bezpieczne. Bezpiecznej kontrolki będą wykonywać we/wy dysku lub nie bezpośrednio uzyskać dostępu do pamięci lub rejestrów komputerze.

Formanty może być oznaczona jako bezpieczne do wykonywania i bezpieczne inicjowanie za pomocą rejestru. Modyfikowanie `DllRegisterServer` dodać wpisy podobne do następujących czynności, aby oznaczyć kontroli jako bezpieczne do wykonywania skryptów i trwałości w rejestrze. Alternatywną metodą jest zaimplementowanie `IObjectSafety`.

Identyfikatory GUID (globalnie unikatowe identyfikatory) będą definiować kontrolki w taki sposób oznaczyć je jako bezpieczny dla skryptów i trwałości. Formanty, które mogą być bezpiecznie inicjowanych przez skrypty będzie zawierać wpis podobny do następującego:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

Formanty, które mogą być bezpiecznie zainicjowane z trwałych danych są oznaczone bezpieczne dla trwałości za pomocą wpisu rejestru podobne do:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

Dodać wpisy podobne do następujących (podstawianie kontroli nad klasy identyfikator zamiast `{06889605-B8D0-101A-91F1-00608CEAD5B3}`) do skojarzenia klucze z następującym Identyfikatorem klasy:

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

##  <a name="_core_licensing_issues"></a> Problemy z licencjonowaniem

Jeśli chcesz użyć licencjonowany formant na stronie sieci Web, należy sprawdzić, umowy licencyjnej umożliwia jego użycia w Internecie i tworzenia pliku pakietu licencji (LPK) dla niego.

Licencjonowany formant ActiveX nie załaduje prawidłowo na stronie HTML w przypadku komputera z uruchomionym programu Internet Explorer nie ma licencji na korzystanie z kontrolki. Na przykład jeśli licencjonowany formant został utworzony przy użyciu języka Visual C++, strony HTML przy użyciu kontrolki zostanie załadowany poprawnie na komputerze, na którym formant został utworzony, ale go nie załaduje na innym komputerze, chyba że informacje o licencjonowaniu jest dołączony.

Aby użyć licencjonowany formant ActiveX w programie Internet Explorer, należy zaznaczyć umowy licencyjnej dostawcy, aby sprawdzić, czy zezwala na licencji dla formantu:

- Redystrybucja

- Użyj formantu w Internecie

- Użycie parametru bazy kodu

Aby użyć licencjonowany formant na stronie HTML na maszynie nonlicensed, należy wygenerować plik pakiet licencji (LPK). Plik LPK zawiera licencji czasu wykonywania dla licencjonowane formanty na stronie HTML. Ten plik został wygenerowany za pomocą LPK_TOOL. Plik EXE, który jest dostarczany z zestawem SDK ActiveX. Aby uzyskać więcej informacji, zobacz witrynę sieci Web MSDN pod [ http://msdn.microsoft.com ](http://msdn.microsoft.com).

#### <a name="to-create-an-lpk-file"></a>Aby utworzyć plik LPK

1. Uruchom LPK_TOOL. Plik EXE na komputerze, którego licencja pozwala na korzystanie z kontrolki.

1. W **narzędzia do tworzenia pakietów licencji** dialogowym **dostępne kontrolki** pola listy, wybierz każdy licencjonowany formant ActiveX, który będzie używany na stronie HTML, a następnie kliknij przycisk **Dodaj**.

1. Kliknij przycisk **Zapisz i Zamknij** i wpisz nazwę dla pliku LPK. Spowoduje to utworzenie pliku LPK i zamknij aplikację.

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Aby osadzić licencjonowany formant na stronie HTML

1. Edytuj stronę HTML. Na stronie HTML Wstaw \<obiektu > tag w przypadku obiektu License Manager przed wszystkimi pozostałymi \<obiektu > tagów. Menedżer licencji jest formant ActiveX, który został zainstalowany przy użyciu programu Internet Explorer. Poniżej przedstawiono jej identyfikator klasy. Ustaw właściwość LPKPath obiektu Menedżer licencji na ścieżkę i nazwę pliku LPK. Może mieć tylko jeden plik LPK na stronie HTML.

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. Wstaw \<obiektu > tag w przypadku usługi licencjonowany formant po tagu Menedżer licencji.

     Na przykład strona HTML, która wyświetla kontrolkę Edycja maskowana firmy Microsoft znajdują się poniżej. Pierwsza klasa, jest identyfikator kontrolki License Manager, druga klasa, którego identyfikator Edycja maskowana kontrolka. Zmienianie tagów, aby wskazywała ścieżkę względną w pliku Lpk, która została utworzona wcześniej i Dodaj tag obiekt, w tym identyfikator klasy formantu.

1. Wstaw \<osadzania > atrybutu dla pliku LPK, jeśli za pomocą wtyczki NCompass ActiveX.

     Kontrolki mogą być wyświetlane na innych aktywnych włączenie przeglądarek — na przykład Netscape przy użyciu wtyczki NCompass ActiveX — należy dodać \<osadzania > składni, jak pokazano poniżej.

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

Aby uzyskać więcej informacji na temat licencjonowania formantów, zobacz [kontrolek ActiveX: Licencjonowanie kontrolki ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md).

##  <a name="_core_signing_code"></a> Podpisywanie kodu

Podpisywanie kodu zaprojektowano w celu zidentyfikowania źródła kodu, a aby zagwarantować, że kod nie zmienił się od czasu jej został podpisany. W zależności od ustawienia zabezpieczeń przeglądarki użytkownicy mogą ostrzegani, przed pobraniem kodu. Użytkownicy mogą wybrać zaufania niektórych właścicieli certyfikatu lub firmy, w których wielkość kod jest podpisywany przy użyciu zaufanego, zostaną pobrane bez ostrzeżenia. Kod jest podpisany cyfrowo, aby zapobiec naruszeniu.

Upewnij się, że kod końcowy jest podpisany, dzięki czemu formant można pobierać automatycznie bez wyświetlania komunikatów ostrzegawczych zaufania. Aby uzyskać szczegółowe informacje na temat podpisywania kodu, zapoznaj się z dokumentacją na Authenticode w zestawie SDK ActiveX i zobacz [podpisanie pliku CAB](/windows/desktop/devnotes/cabinet-api-functions).

W zależności od zaufania i przeglądarki poziomu ustawienia bezpieczeństwa certyfikat może być wyświetlany do identyfikowania podpisywania osoby lub firmy. Jeśli poziom bezpieczeństwa to none lub właściciela certyfikatu z podpisem kontroli jest zaufany, certyfikat nie będą wyświetlane. Zobacz [Internet Explorer przeglądarki bezpieczeństwa poziomy i zachowanie kontrolki](#_core_internet_explorer_browser_safety_levels_and_control_behavior) szczegółowe informacje na temat sposobu ustawienia zabezpieczeń przeglądarki określi, czy formant jest pobierana i certyfikat wyświetlany.

Cyfrowego podpisywania kodu gwarancje nie zmienił się, ponieważ jest on podpisany. Skrót kodu jest wykonywane i osadzone w certyfikacie. Ten skrót później jest porównywany ze skrótu kodu podejmowane po pobraniu kodu, ale zanim zostanie ona uruchomiona. Firmy, takich jak Verisign, można podać prywatnych i publicznych kluczy wymaganych do podpisania kodu. Zestaw SDK ActiveX jest dostarczany za pomocą narzędzia MakeCert, narzędzia do tworzenia Certyfikaty testowe.

##  <a name="_core_managing_the_palette"></a> Zarządzanie palety

Kontenery określić paletę i udostępnić ją jako właściwość otoczenia, **DISPID_AMBIENT_PALETTE**. Kontener (na przykład Internet Explorer) wybiera palety, który jest używany przez wszystkie formanty ActiveX na stronie, aby określić własne palety. To uniemożliwia wyświetlanie migotanie i przedstawia spójny wygląd.

Kontrolki można zastąpić `OnAmbientPropertyChange` do obsługi powiadomień o zmianach wprowadzonych do palety.

Kontrolki można zastąpić `OnGetColorSet` zwrócić zestaw do rysowania z palety kolorów. Kontenery Użyj wartości zwracanej, aby ustalić, czy kontrolka jest obsługujących palety.

W obszarze wytycznych OCX 96 formantu zawsze należy pamiętać swoją paletę w tle.

Starsze kontenerów, które nie korzystają z właściwości otoczenia palety wyśle WM_QUERYNEWPALETTE i WM_PALETTECHANGED wiadomości. Kontrolki można zastąpić `OnQueryNewPalette` i `OnPaletteChanged` do obsługi komunikatów.

##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a> Internet Explorer przeglądarki bezpieczeństwa poziomy i zachowanie kontroli

Przeglądarka ma opcji poziom bezpieczeństwa, które można konfigurować przez użytkownika. Ponieważ stron sieci Web mogą zawierać zawartość aktywna, który może potencjalnie uszkodzić komputer użytkownika, przeglądarek Zezwalaj użytkownikowi na wybranie opcji poziom bezpieczeństwa. W zależności od sposobu, w przeglądarce implementuje poziomy bezpieczeństwa formant nie może zostać pobrana w ogóle lub wyświetli certyfikatu lub komunikat ostrzegawczy, aby zezwolić użytkownikowi na wybranie w czasie wykonywania, czy nie można pobrać formantu. Zachowanie kontrolki ActiveX w obszarze poziomy bezpieczeństwa wysokie, średnie i niskie w programie Internet Explorer znajduje się poniżej.

### <a name="high-safety-mode"></a>Tryb wysokie bezpieczeństwo

- Nie będzie można pobrać formantów bez znaku.

- Podpisane formanty wyświetli certyfikatu, jeśli niezaufanych (użytkownik może wybrać opcję, aby zawsze ufaj od teraz kod z tego właściciela certyfikatu).

- Tylko te formanty, które są oznaczone jako bezpieczne, będzie mieć trwałych danych i/lub można za pomocą skryptów.

### <a name="medium-safety-mode"></a>Tryb bezpieczeństwa średniej

- Niepodpisane kontrolek będą wyświetlać ostrzeżenie przed pobraniem.

- Jeśli zaufany podpisane formanty wyświetli certyfikatu.

- Formanty niezaznaczonych jako bezpieczne zostanie wyświetlone ostrzeżenie.

### <a name="low-safety-mode"></a>Tryb niski poziom zabezpieczeń

- Formanty są pobierane bez ostrzeżenia.

- Obsługa skryptów i trwałości odbywa się bez ostrzeżenia.

## <a name="see-also"></a>Zobacz też

[MFC — zadania związane z programowaniem Internetu](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)<br/>
[Kontrolki ActiveX MFC: licencjonowanie kontrolki ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)

