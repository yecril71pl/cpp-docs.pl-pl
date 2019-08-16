---
title: Uaktualnianie istniejącego formantu ActiveX
ms.date: 09/12/2018
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
ms.openlocfilehash: 06c39240d3718f6fbaa15b46abeb8ac9132b5945
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510864"
---
# <a name="upgrading-an-existing-activex-control"></a>Uaktualnianie istniejącego formantu ActiveX

Istniejące kontrolki ActiveX (wcześniej kontrolki OLE) mogą być używane w Internecie bez modyfikacji. Można jednak zmodyfikować kontrolki, aby zwiększyć ich wydajność.

> [!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

Jeśli używasz kontrolki na stronie sieci Web, istnieją dodatkowe zagadnienia. Plik. ocx i wszystkie pliki pomocnicze muszą znajdować się na maszynie docelowej lub być pobierane przez Internet. Dzięki temu rozmiar kodu i czas pobierania są ważne. Pliki do pobrania można spakować w podpisanym pliku cab. Możesz oznaczyć swój formant jako bezpieczny dla skryptów i jako bezpieczny do inicjowania.

W tym artykule omówiono następujące tematy:

- [Pakowanie kodu do pobrania](#_core_packaging_code_for_downloading)

- [Oznaczanie bezpieczeństwa kontrolki pod kątem obsługi skryptów i inicjowania](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [Problemy z licencjonowaniem](#_core_licensing_issues)

- [Kod podpisywania](#_core_signing_code)

- [Zarządzanie paletą](#_core_managing_the_palette)

- [Poziomy bezpieczeństwa przeglądarki Internet Explorer i zachowanie kontroli](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

Można również dodać optymalizacje, zgodnie z opisem w [kontrolce ActiveX: Optymalizacja](../mfc/mfc-activex-controls-optimization.md). Monikery mogą być używane do pobierania właściwości i dużych obiektów BLOB asynchronicznie, zgodnie z opisem w [kontrolkach ActiveX w Internecie](../mfc/activex-controls-on-the-internet.md).

##  <a name="_core_packaging_code_for_downloading"></a>Pakowanie kodu do pobrania

Aby uzyskać więcej informacji na temat tego tematu, zobacz [pakowanie formantów ActiveX](https://docs.microsoft.com//previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29).

### <a name="the-codebase-tag"></a>Tag CODEBASE

Formanty ActiveX są osadzane na stronach sieci Web `<OBJECT>` przy użyciu znacznika. `CODEBASE` Parametr`<OBJECT>` znacznika określa lokalizację, z której ma zostać pobrany formant. `CODEBASE`może pomyślnie wskazywać kilka różnych typów plików.

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Używanie znacznika CODEBASE z plikiem OCX

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

To rozwiązanie pobiera tylko plik ocx kontrolki i wymaga, aby wszystkie pomocnicze biblioteki DLL zostały już zainstalowane na komputerze klienckim. Ta wartość będzie działała w przypadku formantów ActiveX programu Internet Explorer i C++MFC utworzonych za pomocą wizualizacji, ponieważ program Internet Explorer C++ jest dostarczany z obsługą bibliotek DLL dla formantów wizualnych. Jeśli do wyświetlania tej kontrolki jest używana inna przeglądarka internetowa z obsługą formantów ActiveX, to rozwiązanie nie będzie działać.

### <a name="using-the-codebase-tag-with-an-inf-file"></a>Używanie znacznika CODEBASE z plikiem INF

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

Plik. inf kontroluje instalację pliku ocx i jego plików pomocniczych. Ta metoda nie jest zalecana, ponieważ nie można podpisać pliku inf (zobacz [kod podpisywania](#_core_signing_code) wskaźników przy podpisywaniu kodu).

### <a name="using-the-codebase-tag-with-a-cab-file"></a>Używanie znacznika CODEBASE z plikiem CAB

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

Pliki cabinet są zalecanym sposobem spakowania formantów ActiveX używających MFC. Pakowanie kontrolki ActiveX MFC w pliku cabinet umożliwia dołączenie pliku inf w celu kontrolowania instalacji kontrolki ActiveX i wszystkich zależnych bibliotek DLL (takich jak MFC DLL). Użycie pliku CAB automatycznie kompresuje kod do szybszego pobierania. Jeśli używasz pliku cab do pobrania składnika, można szybciej podpisać cały plik cab niż każdy pojedynczy składnik.

### <a name="creating-cab-files"></a>Tworzenie plików CAB

Narzędzia do tworzenia plików cabinet są teraz częścią [zestawu SDK systemu Windows 10](https://dev.windows.com/downloads/windows-10-sdk).

Plik Cabinet wskazywany przez `CODEBASE` powinien zawierać plik ocx dla kontrolki ActiveX i plik. inf, aby kontrolować jego instalację. Plik Cabinet jest tworzony przez określenie nazwy pliku kontrolnego i pliku inf. Nie dołączaj zależnych bibliotek DLL, które mogą już istnieć w systemie w tym pliku cabinet. Na przykład biblioteki MFC DLL są spakowane w osobnym pliku cabinet i są określane przez kontrolkę pliku inf.

Aby uzyskać szczegółowe informacje na temat sposobu tworzenia pliku CAB, zobacz [Tworzenie pliku cab](/windows/win32/devnotes/cabinet-api-functions).

### <a name="the-inf-file"></a>Plik INF

Poniższy przykład: spindial. inf, wyświetla pliki pomocnicze i informacje o wersji potrzebne do kontrolki MFC spindial. Zauważ, że lokalizacja bibliotek DLL MFC jest witryną sieci Web firmy Microsoft. Mfc42. cab jest dostępny i podpisany przez firmę Microsoft.

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

### <a name="the-object-tag"></a>Tag \<> obiektu

Poniższy przykład ilustruje użycie `<OBJECT>` znacznika do spakowania kontrolki przykładowej MFC spindial.

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

W takim przypadku spindial. cab będzie zawierać dwa pliki, spindial. ocx i spindial. inf. Następujące polecenie spowoduje skompilowanie pliku cabinet:

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

`-s 6144` Parametr rezerwuje miejsce w pliku cabinet do podpisywania kodu.

### <a name="the-version-tag"></a>Tag wersji

Zwróć uwagę, że `#Version` informacje określone za pomocą pliku cab dotyczą kontrolki określonej przez parametr `<OBJECT>` *ClassID* znacznika.

W zależności od podanej wersji można wymusić pobranie formantu. Aby uzyskać pełną specyfikację `OBJECT` tagu, w tym parametr *codebase* , zobacz Dokumentacja W3C.

##  <a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a>Oznaczanie bezpieczeństwa kontrolki pod kątem obsługi skryptów i inicjowania

Kontrolki ActiveX używane na stronach sieci Web powinny być oznaczone jako bezpieczne do obsługi skryptów i bezpieczne do inicjowania, jeśli są w rzeczywistości bezpieczne. Bezpieczna kontrola nie będzie wykonywać operacji we/wy dysku ani bezpośrednio uzyskiwać dostępu do pamięci lub rejestrów na komputerze.

Formanty mogą być oznaczone jako bezpieczne dla skryptów i bezpieczne do inicjowania przy użyciu rejestru. Zmodyfikuj `DllRegisterServer` , aby dodać wpisy podobne do następujących, aby oznaczyć formant jako bezpieczny dla skryptów i trwałości w rejestrze. Alternatywną metodą jest zaimplementowanie `IObjectSafety`.

Zdefiniuj identyfikatory GUID (unikatowe identyfikatory globalne) dla formantu, aby oznaczyć go jako bezpieczny dla skryptów i trwałości. Kontrolki, które mogą być bezpiecznie skrypty, będą zawierać wpis rejestru podobny do następującego:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

Kontrolki, które mogą być bezpiecznie zainicjowane z trwałych danych są oznaczone jako bezpieczne dla trwałości z wpisem rejestru podobnym do:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

Dodaj wpisy podobne do następujących (podstawiając identyfikator `{06889605-B8D0-101A-91F1-00608CEAD5B3}`klasy kontrolki zamiast), aby skojarzyć klucze z następującym identyfikatorem klasy:

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

##  <a name="_core_licensing_issues"></a>Problemy z licencjonowaniem

Jeśli chcesz użyć licencjonowanej kontroli na stronie sieci Web, musisz sprawdzić, czy umowa licencyjna zezwala na korzystanie z Internetu i utworzyć plik pakietu licencji (LPK) dla tego programu.

Licencjonowany formant ActiveX nie zostanie poprawnie załadowany na stronie HTML, jeśli komputer z programem Internet Explorer nie ma licencji na korzystanie z tego formantu. Na przykład jeśli licencjonowana kontrolka została skompilowana przy użyciu C++wizualizacji, strona HTML używająca kontrolki zostanie prawidłowo załadowana na komputerze, na którym kontrolka została skompilowana, ale nie zostanie załadowana na innym komputerze, o ile nie zostaną uwzględnione informacje o licencji.

Aby użyć licencjonowanego formantu ActiveX w programie Internet Explorer, należy sprawdzić umowę licencyjną dostawcy, aby sprawdzić, czy licencja na kontrolkę zezwala:

- Redystrybucja

- Korzystanie z kontrolki w Internecie

- Użycie parametru codebase

Aby skorzystać z licencjonowanej kontrolki na stronie HTML na komputerze bez licencji, należy wygenerować plik pakietu licencji (LPK). Plik LPK zawiera licencje w czasie wykonywania licencjonowanych formantów na stronie HTML. Ten plik jest generowany przez LPK_TOOL. EXE, który jest dostarczany z zestawem SDK ActiveX.

#### <a name="to-create-an-lpk-file"></a>Aby utworzyć plik LPK

1. Uruchom LPK_TOOL. Program EXE na komputerze, który ma licencję na korzystanie z tego formantu.

1. W oknie dialogowym **narzędzie autorskie pakietu licencji** w polu listy **dostępne kontrolki** zaznacz każdy licencjonowany formant ActiveX, który będzie używany na stronie HTML, a następnie kliknij przycisk **Dodaj**.

1. Kliknij przycisk **zapisz & Exit** i wpisz nazwę pliku lpk. Spowoduje to utworzenie pliku LPK i zamknięcie aplikacji.

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Aby osadzić licencjonowaną kontrolę na stronie HTML

1. Edytuj stronę HTML. Na stronie HTML Wstaw \<tag > obiektu dla obiektu Menedżera licencji przed wszystkimi innymi \<tagami > obiektu. Menedżer licencji to formant ActiveX, który jest instalowany z programem Internet Explorer. Identyfikator klasy jest przedstawiony poniżej. Ustaw właściwość LPKPath obiektu Menedżera licencji na ścieżkę i nazwę pliku LPK. Na stronie HTML może znajdować się tylko jeden plik LPK.

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. Wstaw tag > obiektu dla licencjonowanej kontrolki po tagu Menedżera licencji. \<

   Przykładowo poniżej zostanie wyświetlona strona HTML, która wyświetla formant edycji z maską firmy Microsoft. Pierwszy identyfikator klasy jest przeznaczony dla kontrolki Menedżer licencji, drugi identyfikator klasy jest przeznaczony do kontrolki edycji maskowanej. Zmień znaczniki tak, aby wskazywały ścieżkę względną utworzonego wcześniej pliku. lpk, i Dodaj tag obiektu, w tym identyfikator klasy dla kontrolki.

1. Wstaw atrybut \<embed > dla pliku lpk, jeśli jest używana wtyczka ActiveX NCompass.

   Jeśli kontrolka może być wyświetlana w innych aktywnych przeglądarkach, na przykład w programie Netscape przy użyciu wtyczki ActiveX NCompass, należy dodać \<składnię osadzania >, jak pokazano poniżej.

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

Aby uzyskać więcej informacji na temat kontroli licencjonowania [, zobacz kontrolki ActiveX: Licencjonowanie kontrolki](../mfc/mfc-activex-controls-licensing-an-activex-control.md)ActiveX.

##  <a name="_core_signing_code"></a>Kod podpisywania

Podpisywanie kodu służy do identyfikowania źródła kodu i do zagwarantowania, że kod nie został zmieniony od czasu podpisania. W zależności od ustawień bezpieczeństwa przeglądarki, użytkownicy mogą być ostrzegani przed pobraniem kodu. Użytkownicy mogą zdecydować się na ufanie określonym właścicielom lub firmom certyfikatu, w którym kod przypadku podpisany przez zaufanych użytkowników zostanie pobrany bez ostrzeżenia. Kod jest podpisany cyfrowo, aby uniknąć manipulowania.

Upewnij się, że końcowy kod jest podpisany, aby można było automatycznie pobrać formant bez wyświetlania komunikatów ostrzegawczych zaufania. Aby uzyskać szczegółowe informacje na temat podpisywania kodu, zapoznaj się z dokumentacją dotyczącą technologii Authenticode w zestawie SDK ActiveX i zobacz Podpisywanie [pliku cab](/windows/win32/devnotes/cabinet-api-functions).

W zależności od ustawień poziomu zabezpieczeń zaufania i przeglądarki certyfikat może być wyświetlany w celu zidentyfikowania osoby podpisującej lub firmy. Jeśli poziom bezpieczeństwa ma wartość Brak lub właściciel certyfikatu podpisanej kontrolki jest zaufany, certyfikat nie zostanie wyświetlony. Zobacz [poziomy bezpieczeństwa przeglądarki Internet Explorer i zachowanie kontroli,](#_core_internet_explorer_browser_safety_levels_and_control_behavior) Aby uzyskać szczegółowe informacje na temat sposobu, w jaki ustawienia bezpieczeństwa przeglądarki określają, czy kontrolka została pobrana i czy jest wyświetlany certyfikat.

Kod gwarancji podpisywania cyfrowego nie zmienił się od czasu podpisania. Skrót kodu jest pobierany i osadzony w certyfikacie. Ten skrót jest później porównywany z wartością skrótu kodu pobranego po pobraniu kodu, ale przed jego uruchomieniem. Firmy, takie jak VeriSign, mogą dostarczyć prywatnych i publicznych kluczy wymaganych do podpisywania kodu. Zestaw SDK ActiveX jest dostarczany z MakeCert, a narzędzie do tworzenia certyfikatów testowych.

##  <a name="_core_managing_the_palette"></a>Zarządzanie paletą

Kontenery określają paletę i udostępniają ją jako Właściwość otoczenia, **DISPID_AMBIENT_PALETTE**. Kontener (na przykład Internet Explorer) wybiera paletę używaną przez wszystkie kontrolki ActiveX na stronie, aby określić własną paletę. Zapobiega to wyświetlaniu migotania i przedstawia spójny wygląd.

Kontrolka może przesłonić `OnAmbientPropertyChange` , aby obsługiwać powiadomienia o zmianach w palecie.

Kontrolka może przesłonić `OnGetColorSet` w celu zwrócenia zestawu kolorów w celu narysowania palety. Kontenery używają wartości zwracanej, aby określić, czy formant jest oparty na palecie.

W obszarze wskazówki dotyczące OCX 96 formant musi zawsze korzystać z palety w tle.

Starsze kontenery, które nie używają właściwości otaczającej paletę, będą wysyłać wiadomości WM_QUERYNEWPALETTE i WM_PALETTECHANGED. Kontrolka może przesłonić `OnQueryNewPalette` i `OnPaletteChanged` obsłużyć te komunikaty.

##  <a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a>Poziomy bezpieczeństwa przeglądarki Internet Explorer i zachowanie kontroli

W przeglądarce są dostępne opcje poziomu zabezpieczeń, które można konfigurować przez użytkownika. Ze względu na to, że strony sieci Web mogą zawierać aktywną zawartość, która może potencjalnie uszkodzić komputer użytkownika, przeglądarki umożliwiają użytkownikowi wybranie opcji poziomu bezpieczeństwa. W zależności od sposobu, w jaki przeglądarka implementuje poziomy bezpieczeństwa, kontrolka może nie być pobierana w ogóle lub zostanie wyświetlony certyfikat lub komunikat ostrzegawczy, aby umożliwić użytkownikowi wybranie w czasie wykonywania niezależnie od tego, czy formant ma być pobierany. Poniżej przedstawiono zachowanie formantów ActiveX w obszarze wysoki, średni i niski poziom bezpieczeństwa w programie Internet Explorer.

### <a name="high-safety-mode"></a>Tryb wysokiej ochrony

- Niepodpisane kontrolki nie zostaną pobrane.

- Kontrolki podpisane będą wyświetlały certyfikat w przypadku niezaufanego (użytkownik może wybrać opcję Zawsze ufaj kodowi od tego właściciela certyfikatu od teraz na).

- Tylko kontrolki oznaczone jako bezpieczne będą miały trwałe dane i/lub mogą być skrypty.

### <a name="medium-safety-mode"></a>Średni tryb zabezpieczeń

- Kontrolki bez znaku będą wyświetlały ostrzeżenie przed pobraniem.

- Kontrolki podpisane będą wyświetlać certyfikat w przypadku niezaufanego.

- Kontrolki, które nie są oznaczone jako bezpieczne, będą wyświetlały ostrzeżenie.

### <a name="low-safety-mode"></a>Tryb niskiego poziomu zabezpieczeń

- Kontrolki są pobierane bez ostrzeżenia.

- Wykonywanie skryptów i trwałość bez ostrzeżenia.

## <a name="see-also"></a>Zobacz także

[MFC — zadania związane z programowaniem Internetu](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)<br/>
[Kontrolki ActiveX MFC: licencjonowanie kontrolki ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)
