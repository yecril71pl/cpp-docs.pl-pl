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
ms.openlocfilehash: dfee42369b698956f4f91ab61a1f37e0ef06d9f1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754504"
---
# <a name="upgrading-an-existing-activex-control"></a>Uaktualnianie istniejącego formantu ActiveX

Istniejące formanty ActiveX (dawniej formanty OLE) mogą być używane w Internecie bez modyfikacji. Jednak można zmodyfikować formanty, aby poprawić ich wydajność.

> [!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

Podczas korzystania z formantu na stronie sieci Web, istnieją dodatkowe zagadnienia. Plik .ocx i wszystkie pliki pomocnicze muszą znajdować się na komputerze docelowym lub zostać pobrane przez Internet. To sprawia, że rozmiar kodu i czas pobierania ważnym czynnikiem. Pliki do pobrania można zapakować w podpisany plik cab. Możesz oznaczyć formant jako bezpieczny dla skryptów i jako bezpieczny do inicjowania.

W tym artykule omówiono następujące tematy:

- [Kod opakowania do pobrania](#_core_packaging_code_for_downloading)

- [Oznaczanie bezpiecznego sterowania do skryptów i inicjowania](#_core_marking_a_control_safe_for_scripting_and_initializing)

- [Problemy z licencjonowaniem](#_core_licensing_issues)

- [Kod podpisywania](#_core_signing_code)

- [Zarządzanie paletą](#_core_managing_the_palette)

- [Poziomy bezpieczeństwa przeglądarki internet explorer i zachowanie kontroli](#_core_internet_explorer_browser_safety_levels_and_control_behavior)

Można również dodać optymalizacje, zgodnie z opisem w [ActiveX Controls: Optimization](../mfc/mfc-activex-controls-optimization.md). Monikers mogą być używane do pobierania właściwości i dużych bloków BLOB asynchronicznie, jak opisano w [ActiveX Kontroli](../mfc/activex-controls-on-the-internet.md)w Internecie .

## <a name="packaging-code-for-downloading"></a><a name="_core_packaging_code_for_downloading"></a>Kod opakowania do pobrania

Aby uzyskać więcej informacji na ten temat, zobacz [Pakowanie formantów ActiveX](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa751974%28v%3dvs.85%29).

### <a name="the-codebase-tag"></a>The CODEBASE Tag

Formanty ActiveX są osadzone `<OBJECT>` na stronach sieci Web przy użyciu znacznika. Parametr `CODEBASE` tagu `<OBJECT>` określa lokalizację, z której ma być pobierany formant. `CODEBASE`może wskazać wiele różnych typów plików pomyślnie.

### <a name="using-the-codebase-tag-with-an-ocx-file"></a>Używanie znacznika CODEBASE z plikiem OCX

```
CODEBASE="http://example.microsoft.com/mycontrol.ocx#version=4,
    70,
    0,
    1086"
```

To rozwiązanie pobiera tylko plik ocx formantu i wymaga, aby wszystkie obsługujące biblioteki DLL były już zainstalowane na komputerze klienckim. Będzie to działać dla formantów Programu Internet Explorer i MFC ActiveX utworzonych za pomocą programu Visual C++, ponieważ program Internet Explorer jest dostarczany z obsługiwanymi bibliotekami DLL dla formantów języka Visual C++. Jeśli do wyświetlania tego formantu używana jest inna przeglądarka internetowa obsługująca kontrolę ActiveX, to rozwiązanie nie będzie działać.

### <a name="using-the-codebase-tag-with-an-inf-file"></a>Używanie znacznika CODEBASE z plikiem INF

```
CODEBASE="http://example.microsoft.com/trustme.inf"
```

Plik .inf będzie kontrolował instalację pliku .ocx i jego plików pomocniczych. Ta metoda nie jest zalecana, ponieważ nie jest możliwe podpisanie pliku .inf (zobacz [Podpisywanie kodu](#_core_signing_code) dla wskaźników podpisywania kodu).

### <a name="using-the-codebase-tag-with-a-cab-file"></a>Używanie znacznika CODEBASE z plikiem CAB

```
CODEBASE="http://example.microsoft.com/acontrol.cab#version=1,
    2,
    0,
    0"
```

Pliki cabinet są zalecanym sposobem pakowania formantów ActiveX, które używają MFC. Pakowanie formantu MFC ActiveX w pliku cabinet umożliwia dołączanie pliku .inf do sterowania instalacją formantu ActiveX i wszelkich zależnych bibliotek DLL (takich jak biblioteki DLL MFC). Użycie pliku CAB automatycznie kompresuje kod w celu szybszego pobrania. Jeśli używasz pliku cab do pobierania składników, szybsze jest podpisanie całego pliku cab niż każdy pojedynczy składnik.

### <a name="creating-cab-files"></a>Tworzenie plików CAB

Narzędzia do tworzenia plików szafek są teraz częścią [zestawu Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk).

Wskazany plik `CODEBASE` gabinetu powinien zawierać plik ocx dla formantu ActiveX i plik .inf, aby kontrolować jego instalację. Plik gabinetu można utworzyć, określając nazwę pliku kontrolnego i pliku .inf. Nie należy dołączać zależnych bibliotek DLL, które mogą już istnieć w systemie w tym pliku szafy. Na przykład biblioteki DLL MFC są pakowane w oddzielny plik gabinetu i określane przez kontrolujący plik .inf.

Aby uzyskać szczegółowe informacje na temat tworzenia pliku CAB, zobacz [Tworzenie pliku CAB](/windows/win32/devnotes/cabinet-api-functions).

### <a name="the-inf-file"></a>Plik INF

Poniższy przykład spindial.inf, zawiera listę plików pomocniczych i informacje o wersji potrzebne dla MFC Spindial kontroli. Zwróć uwagę, że lokalizacja bibliotek DLL MFC jest witryną firmy Microsoft w sieci Web. Mfc42.cab jest dostarczany i podpisany przez firmę Microsoft.

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

### <a name="the-object-tag"></a>Znacznik \<> OBJECT

Poniższy przykład ilustruje przy użyciu tagu `<OBJECT>` do pakowania MFC spindial kontroli próbki.

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

W takim przypadku spindial.cab będzie zawierać dwa pliki, spindial.ocx i spindial.inf. Następujące polecenie spowoduje zbudowanie pliku gabinetu:

```
C:\CabDevKit\cabarc.exe -s 6144 N spindial.cab spindial.ocx spindial.inf
```

Parametr `-s 6144` rezerwuje miejsce w szafce na podpisywanie kodu.

### <a name="the-version-tag"></a>Tag wersji

Należy zauważyć, `#Version` że informacje określone za pomocą pliku CAB ma zastosowanie `<OBJECT>` do formantu określonego przez parametr *CLASSID* tagu.

W zależności od określonej wersji można wymusić pobranie formantu. Aby uzyskać pełną `OBJECT` specyfikację tagu, w tym parametr *CODEBASE,* zobacz odwołanie do W3C.

## <a name="marking-a-control-safe-for-scripting-and-initializing"></a><a name="_core_marking_a_control_safe_for_scripting_and_initializing"></a>Oznaczanie bezpiecznego sterowania do skryptów i inicjowania

Formanty ActiveX używane na stronach sieci Web powinny być oznaczone jako bezpieczne do tworzenia skryptów i bezpieczne do inicjowania, jeśli są one w rzeczywistości bezpieczne. Bezpieczny formant nie wykona we/wy dysku ani nie będzie bezpośrednio uzyskiwać dostępu do pamięci lub rejestrów komputera.

Formanty mogą być oznaczone jako bezpieczne dla skryptów i bezpieczne do inicjowania za pośrednictwem rejestru. Zmodyfikuj, `DllRegisterServer` aby dodać wpisy podobne do poniższych, aby oznaczyć formant jako bezpieczny dla skryptów i trwałości w rejestrze. Alternatywną metodą `IObjectSafety`jest wdrożenie .

Identyfikatory GUID (Global Unique Identifiers) zostaną zdefiniowane dla formantu, aby oznaczyć je jako bezpieczne dla skryptów i trwałości. Formanty, które mogą być bezpiecznie skryptowane będzie zawierać wpis rejestru podobne do następujących:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
```

Formanty, które można bezpiecznie zainicjować z danych trwałych są oznaczone jako bezpieczne dla trwałości z wpisem rejestru podobnym do:

```
HKEY_CLASSES_ROOT\Component Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

Dodaj wpisy podobne do następujących (zastępując identyfikator klasy formantu `{06889605-B8D0-101A-91F1-00608CEAD5B3}`zamiast), aby skojarzyć klucze z następującym identyfikatorem klasy:

```
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}
HKEY_CLASSES_ROOT\CLSID\{06889605-B8D0-101A-91F1-00608CEAD5B3}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}
```

## <a name="licensing-issues"></a><a name="_core_licensing_issues"></a>Problemy z licencjonowaniem

Jeśli chcesz użyć licencjonowanego formantu na stronie sieci Web, musisz sprawdzić, czy umowa licencyjna zezwala na jej użycie w Internecie i utworzyć dla niej plik pakietu licencji (LPK).

Licencjonowany formant ActiveX nie zostanie poprawnie załadowany na stronie HTML, jeśli komputer z programem Internet Explorer nie ma licencji na używanie formantu. Na przykład jeśli licencjonowany formant został zbudowany przy użyciu języka Visual C++, strona HTML przy użyciu formantu zostanie poprawnie załadowana na komputerze, na którym formant został zbudowany, ale nie zostanie załadowana na innym komputerze, chyba że zostaną dołączone informacje o licencjonowaniu.

Aby użyć licencjonowanego formantu ActiveX w programie Internet Explorer, należy sprawdzić umowę licencyjną dostawcy, aby sprawdzić, czy licencja formantu zezwala na:

- Redystrybucja

- Korzystanie z kontroli w Internecie

- Użycie parametru Codebase

Aby użyć licencjonowanego formantu na stronie HTML na komputerze bez licencji, należy wygenerować plik pakietu licencji (LPK). Plik LPK zawiera licencje w czasie wykonywania licencjonowanych formantów na stronie HTML. Ten plik jest generowany za pośrednictwem LPK_TOOL. EXE, który jest dostarczany z activex SDK.

#### <a name="to-create-an-lpk-file"></a>Aby utworzyć plik LPK

1. Uruchom LPK_TOOL. EXE na komputerze, który jest licencjonowany do korzystania z formantu.

1. W oknie dialogowym **Narzędzie do tworzenia pakietów licencji** w polu listy Dostępne **formanty** zaznacz każdy licencjonowany formant ActiveX, który będzie używany na stronie HTML, a następnie kliknij przycisk **Dodaj**.

1. Kliknij **pozycję Zapisz & Zakończ** i wpisz nazwę pliku LPK. Spowoduje to utworzenie pliku LPK i zamknięcie aplikacji.

#### <a name="to-embed-a-licensed-control-on-an-html-page"></a>Aby osadzić licencjonowany formant na stronie HTML

1. Edytuj stronę HTML. Na stronie HTML wstaw znacznik \<OBJECT> dla obiektu Menedżera \<licencji przed innymi znacznikami object>. Menedżer licencji jest formantem ActiveX zainstalowanym w programie Internet Explorer. Jego identyfikator klasy jest pokazany poniżej. Ustaw właściwość LPKPath obiektu Menedżera licencji na ścieżkę i nazwę pliku LPK. Na stronie HTML można mieć tylko jeden plik LPK.

```
<OBJECT CLASSID = "clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="relative URL to .LPK file">
</OBJECT>
```

1. Wstaw \<tag OBJECT> dla licencjonowanego formantu po tagu Menedżera licencji.

   Na przykład strona HTML, na którą jest wyświetlana kontrolka Edycji Maskowanego firmy Microsoft, jest wyświetlana poniżej. Pierwszy identyfikator klasy jest dla Menedżera licencji kontroli, drugi identyfikator klasy jest dla maskowane edit kontroli. Zmień znaczniki, aby wskazywały ścieżkę względną pliku .lpk utworzonego wcześniej, i dodaj znacznik obiektu zawierający identyfikator klasy dla formantu.

1. Wstaw \<atrybut EMBED> dla pliku LPK, jeśli używasz wtyczki NCompass ActiveX.

   Jeśli formant może być wyświetlany w innych przeglądarkach z włączoną obsługą Active — na przykład netscape za pomocą wtyczki NCompass ActiveX — należy dodać składnię \<EMBED>, jak pokazano poniżej.

```
<OBJECT CLASSID="clsid:5220cb21-c88d-11cf-b347-00aa00a28331">
<PARAM NAME="LPKPath" VALUE="maskedit.lpk">

<EMBED SRC = "maskedit.LPK">

</OBJECT>
<OBJECT CLASSID="clsid:C932BA85-4374-101B-A56C-00AA003668DC" WIDTH=100 HEIGHT=25>
</OBJECT>
```

Aby uzyskać więcej informacji na temat licencjonowania sterowania, zobacz [ActiveX Controls: Licensing an ActiveX Control](../mfc/mfc-activex-controls-licensing-an-activex-control.md).

## <a name="signing-code"></a><a name="_core_signing_code"></a>Kod podpisywania

Podpisywanie kodu jest przeznaczony do identyfikowania źródła kodu i gwarancji, że kod nie uległ zmianie od czasu podpisania. W zależności od ustawień bezpieczeństwa przeglądarki użytkownicy mogą być ostrzegani przed pobraniem kodu. Użytkownicy mogą zaufać niektórym właścicielom certyfikatów lub firmom, w którym to przypadku kod podpisany przez zaufanych zostanie pobrany bez ostrzeżenia. Kod jest podpisany cyfrowo, aby uniknąć manipulacji.

Upewnij się, że ostateczny kod jest podpisany, dzięki czemu formant może być automatycznie pobierany bez wyświetlania komunikatów ostrzegawczych zaufania. Szczegółowe informacje na temat podpisywania kodu można znaleźć w dokumentacji authenticode w pliku ActiveX SDK i zobacz [Podpisywanie pliku CAB](/windows/win32/devnotes/cabinet-api-functions).

W zależności od ustawień poziomu zaufania i poziomu bezpieczeństwa przeglądarki może zostać wyświetlony certyfikat identyfikujący osobę podpisującą lub firmę. Jeśli poziom bezpieczeństwa jest brak, lub jeśli właściciel certyfikatu podpisanego formantu jest zaufany, certyfikat nie zostanie wyświetlony. Zobacz [Poziomy bezpieczeństwa przeglądarki Internet Explorer i zachowanie kontroli, aby](#_core_internet_explorer_browser_safety_levels_and_control_behavior) uzyskać szczegółowe informacje na temat sposobu, w jaki ustawienie bezpieczeństwa przeglądarki określi, czy formant jest pobierany i wyświetlany jest certyfikat.

Podpisywanie cyfrowe gwarantuje, że kod nie zmienił się od momentu podpisania. Skrót kodu jest pobierana i osadzona w certyfikacie. Ten skrót jest później porównywany z skrótem kodu pobranego po pobraniu kodu, ale przed jego uruchomieniu. Firmy takie jak Verisign mogą dostarczać klucze prywatne i publiczne potrzebne do podpisania kodu. ActiveX SDK jest dostarczany z MakeCert, narzędziem do tworzenia certyfikatów testowych.

## <a name="managing-the-palette"></a><a name="_core_managing_the_palette"></a>Zarządzanie paletą

Kontenery określają paletę i udostępniają ją jako właściwość **otoczenia, DISPID_AMBIENT_PALETTE**. Kontener (na przykład Program Internet Explorer) wybiera paletę używaną przez wszystkie formanty ActiveX na stronie w celu określenia własnej palety. Zapobiega to migotaniu ekranu i zapewnia spójny wygląd.

Formant może zastąpić `OnAmbientPropertyChange` do obsługi powiadomień o zmianach w palecie.

Formant może `OnGetColorSet` zastąpić, aby zwrócić zestaw kolorów, aby narysować paletę. Kontenery używają zwracanej wartości, aby określić, czy formant jest obsługujący paletę.

Zgodnie z wytycznymi OCX 96 formant musi zawsze realizować swoją paletę w tle.

Starsze kontenery, które nie używają właściwości palety otoczenia, będą wysyłać WM_QUERYNEWPALETTE i WM_PALETTECHANGED komunikatów. Formant może zastąpić `OnQueryNewPalette` `OnPaletteChanged` i obsługiwać te komunikaty.

## <a name="internet-explorer-browser-safety-levels-and-control-behavior"></a><a name="_core_internet_explorer_browser_safety_levels_and_control_behavior"></a>Poziomy bezpieczeństwa przeglądarki internet explorer i zachowanie kontroli

Przeglądarka ma opcje poziomu bezpieczeństwa, konfigurowane przez użytkownika. Ponieważ strony sieci Web mogą zawierać aktywną zawartość, która może potencjalnie uszkodzić komputer użytkownika, przeglądarki umożliwiają użytkownikowi wybranie opcji poziomu bezpieczeństwa. W zależności od sposobu, w jaki przeglądarka implementuje poziomy bezpieczeństwa, formant może nie zostać pobrany w ogóle lub wyświetli certyfikat lub komunikat ostrzegawczy, aby umożliwić użytkownikowi wybranie w czasie wykonywania, czy pobrać formant. Zachowanie formantów ActiveX w programie Internet Explorer pod wysokim, średnim i niskim poziomem bezpieczeństwa jest wymienione poniżej.

### <a name="high-safety-mode"></a>Tryb wysokiego bezpieczeństwa

- Niepodpisane formanty nie zostaną pobrane.

- Podpisane formanty będą wyświetlać certyfikat, jeśli jest niezaufany (użytkownik może wybrać opcję, aby zawsze ufać kodowi od tego właściciela certyfikatu od teraz).

- Tylko formanty oznaczone jako bezpieczne będą miały trwałe dane i/lub będą możliwe do skryptów.

### <a name="medium-safety-mode"></a>Średni tryb bezpieczeństwa

- Niepodpisane formanty wyświetlają ostrzeżenie przed pobraniem.

- Podpisane formanty będą wyświetlać certyfikat, jeśli jest niezaufany.

- Formanty nieoznaczone jako bezpieczne wyświetlają ostrzeżenie.

### <a name="low-safety-mode"></a>Tryb niskiego bezpieczeństwa

- Formanty są pobierane bez ostrzeżenia.

- Skrypty i trwałość występują bez ostrzeżenia.

## <a name="see-also"></a>Zobacz też

[MFC — zadania związane z programowaniem Internetu](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)<br/>
[Kontrolki ActiveX MFC: licencjonowanie kontrolki ActiveX](../mfc/mfc-activex-controls-licensing-an-activex-control.md)
