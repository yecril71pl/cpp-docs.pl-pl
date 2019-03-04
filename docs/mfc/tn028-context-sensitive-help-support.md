---
title: 'TN028: Obsługa pomocy kontekstowej'
ms.date: 11/04/2016
f1_keywords:
- vc.help
helpviewer_keywords:
- context-sensitive Help [MFC], MFC applications
- TN028
- resource identifiers, context-sensitive Help
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
ms.openlocfilehash: e3ac2742f2c57c01c645c72c933234a96ece773a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288288"
---
# <a name="tn028-context-sensitive-help-support"></a>TN028: Obsługa pomocy kontekstowej

Ta uwaga opisuje zasady przypisywania identyfikatorów kontekstów pomocy i innych problemów pomocy w MFC. Obsługa pomocy kontekstowej wymaga kompilatora plików pomocy, które są dostępne w programie Visual C++.

> [!NOTE]
>  Oprócz wykonywania za pomocą WinHelp pomocy kontekstowej, biblioteka MFC obsługuje korzystanie z pomocy HTML. Aby uzyskać więcej informacji na temat tej pomocy technicznej i programowania, korzystając z pomocy HTML, zobacz [Pomoc HTML: Pomoc kontekstowa do programów](../mfc/html-help-context-sensitive-help-for-your-programs.md).

## <a name="types-of-help-supported"></a>Typy obsługiwane pomocy

Istnieją dwa rodzaje pomocy kontekstowej zaimplementowane w aplikacjach Windows. Pierwsza strona, określane jako "F1 Pomoc" obejmuje uruchamianie WinHelp z odpowiedniego kontekstu na podstawie aktualnie aktywnego obiektu. Drugim jest tryb "Shift + F1". W tym trybie kursor myszy zmieni się w kursor pomocy, a użytkownik przechodzi do kliknij obiekt. W tym momencie WinHelp zostanie uruchomiona, aby udzielić pomocy dla obiektu, który użytkownik kliknął.

Microsoft Foundation Classes zaimplementować obu formach pomocy. Ponadto platforma obsługuje dwa polecenia pomocy prostego indeksu Pomocy i korzystanie z pomocy.

## <a name="help-files"></a>Pliki pomocy

Microsoft Foundation classes założono pojedynczego pliku pomocy. Ten plik pomocy musi mieć taką samą nazwę i ścieżkę aplikacji. Na przykład jeśli plik wykonywalny narzędzia nosi C:\MyApplication\MyHelp.exe plik pomocy należy C:\MyApplication\MyHelp.hlp. Ustaw ścieżkę za pośrednictwem *m_pszHelpFilePath* zmienną elementu członkowskiego [klasa CWinApp](../mfc/reference/cwinapp-class.md).

## <a name="help-context-ranges"></a>Zakresy kontekstu pomocy

Domyślna implementacja MFC wymaga program do wykonania niektórych reguł dotyczących przypisania Pomoc kontekstowa identyfikatorów. Te zasady są zakres identyfikatorów przydzielone do określonych formantów. Te reguły można zastąpić, podając różne implementacje różnych funkcji związanych z elementu członkowskiego.

```
0x00000000 - 0x0000FFFF : user defined
0x00010000 - 0x0001FFFF : commands (menus/command buttons)
0x00010000 + ID_
(note: 0x18000-> 0x1FFFF is the practical range since command IDs are>=0x8000)
0x00020000 - 0x0002FFFF : windows and dialogs
0x00020000 + IDR_
(note: 0x20000-> 0x27FFF is the practical range since IDRs are <= 0x7FFF)
0x00030000 - 0x0003FFFF : error messages (based on error string ID)
0x00030000 + IDP_
0x00040000 - 0x0004FFFF : special purpose (non-client areas)
0x00040000 + HitTest area
0x00050000 - 0x0005FFFF : controls (those that are not commands)
0x00040000 + IDW_
```

## <a name="simple-help-commands"></a>Proste "Help" poleceń

Istnieją dwóch prostych poleceń pomocy, które są implementowane przez klasy Microsoft Foundation:

- Id_help_index —, który jest implementowany przez [CWinApp::OnHelpIndex](../mfc/reference/cwinapp-class.md#onhelpindex)

- Id_help_using —, który jest implementowany przez [CWinApp::OnHelpUsing](../mfc/reference/cwinapp-class.md#onhelpusing)

Pierwsze polecenie wyświetla indeks pomocy dla aplikacji. Drugi zawiera pomoc dla użytkowników za pomocą programu pomocy systemu Windows.

## <a name="context-sensitive-help-f1-help"></a>Pomoc kontekstowa (pomocy F1)

Klawisz F1 jest zwykle tłumaczyć polecenia przy użyciu Identyfikatora elementu id_help — akceleratora, który został umieszczony w głównym oknie tabeli akceleratora. Id_help — polecenie może być też generowane przez przycisk z Identyfikatorem programu id_help — w głównym oknie lub okienku dialogowym.

Niezależnie od tego, jak jest generowany id_help — polecenie zostanie skierowany w ramach normalnych polecenia aż do napotkania procedurę obsługi poleceń. Aby uzyskać więcej informacji na temat architektury routing poleceń MFC dotyczą [techniczne 21 Uwaga](../mfc/tn021-command-and-message-routing.md). Jeśli aplikacja ma włączone pomocy, id_help — polecenie będzie obsługiwany przez [CWinApp::OnHelp](../mfc/reference/cwinapp-class.md#onhelp). Aplikacja otrzymuje komunikat pomocy, a następnie przekierowuje odpowiednio polecenia. Jest to konieczne, ponieważ domyślny routing poleceń nie jest odpowiednia do określenia najbardziej specyficznego kontekstu.

`CWinApp::OnHelp` próbuje uruchomić WinHelp w następującej kolejności:

1. Sprawdza, czy aktywna `AfxMessageBox` wywołania z identyfikatorem pomocy. Jeśli okno komunikatu jest obecnie aktywny, WinHelp jest uruchamiany w kontekście, które są odpowiednie dla tego pola komunikatu.

1. Wysyła komunikat WM_COMMANDHELP aktywnego okna. Jeśli to okno nie odpowiada, uruchamiając WinHelp, ten sam komunikat zostanie przesłany do elementów nadrzędnych tego okna, dopóki komunikat jest przetwarzany lub bieżące okno jest oknem najwyższego poziomu.

1. Wysyła polecenie id_default_help — do głównego okna. Wywołuje to domyślna Pomoc. To polecenie jest zwykle mapowane `CWinApp::OnHelpIndex`.

Aby zastąpić globalny identyfikator podstawowej wartości domyślne (np. 0x10000 dla poleceń i 0x20000 dla zasobów, takich jak okna dialogowe), należy zastąpić aplikacji [CWinApp::WinHelp](../mfc/reference/cwinapp-class.md#winhelp).

Aby zastąpić tę funkcję i sposób, że kontekstu pomocy jest określana, powinna obsługiwać WM_COMMANDHELP wiadomości. Możesz zapewniają bardziej szczegółowe pomocy routing niż zapewnia platformę, ponieważ tylko przechodzi ona szczegółowe jako bieżące okno podrzędne MDI. Można też dostarczać dokładniejsze Pomoc dla określonego okna lub okno dialogowe, może być oparte na bieżący stan wewnętrzny tego obiektu lub aktywny formant w oknie dialogowym.

## <a name="wmcommandhelp"></a>WM_COMMANDHELP

```

afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)
```

WM_COMMANDHELP jest prywatny Windows MFC odebrana przez aktywne okno zleconą pomocy. Gdy okno odbiera ten komunikat, może wywołać `CWinApp::WinHelp` z kontekstu, który pasuje wewnętrzny stan okna.

*lParam*<br/>
Zawiera obecnie dostępna Pomoc kontekstowa. *lParam* wynosi zero, jeśli stwierdził brak kontekstu pomocy. Implementacja `OnCommandHelp` można użyć Identyfikatora kontekstu w *lParam* do określenia innego kontekstu lub po prostu przekazać go do `CWinApp::WinHelp`.

*wParam*<br/>
Nie jest używana i będzie mieć wartość zero.

Jeśli `OnCommandHelp` wywołaniach funkcji `CWinApp::WinHelp`, powinien zostać zwrócony **TRUE**. Zwracanie **TRUE** Zatrzymuje routing to polecenie dla innych klas i innych oknach.

## <a name="help-mode-shiftf1-help"></a>Tryb Help (Pomoc Shift + F1)

Jest to druga forma pomocy kontekstowej. Ogólnie rzecz biorąc w tym trybie jest wprowadzana przez naciśnięcie klawisza SHIFT + F1 lub za pośrednictwem menu/na pasku narzędzi. Są one zaimplementowane jako polecenia (id_context_help —). Hook filtr komunikatu nie jest używana do translacji tego polecenia podczas modalne okno dialogowe lub menu jest aktywna, w związku z tym to polecenie jest dostępna tylko dla użytkownika, gdy aplikacja wykonuje pompy komunikatów głównego (`CWinApp::Run`).

Po wprowadzeniu tego trybu, kursor myszy pomocy jest wyświetlany za pośrednictwem wszystkich obszarów aplikacji, nawet wtedy, gdy aplikacja normalnie zostanie wyświetlony swój własny kursor dla tego obszaru, (na przykład rozmiaru obramowania okna). Użytkownik będzie mógł wybierz polecenie za pomocą myszy lub klawiatury. Zamiast wykonywania polecenia, zostanie wyświetlona Pomoc dotyczącą tego polecenia. Ponadto użytkownik może kliknąć obiekt widoczne na ekranie, takiej jak przycisk na pasku narzędzi i będzie można wyświetlić pomocy dla tego obiektu. Ten tryb pomocy są dostarczane przez `CWinApp::OnContextHelp`.

Podczas wykonywania tej pętli wszystkich za pomocą klawiatury w danych wejściowych jest nieaktywny, z wyjątkiem klucze uzyskujących dostęp do menu. Ponadto tłumaczenia polecenia nadal jest realizowana za pośrednictwem `PreTranslateMessage` Aby zezwolić użytkownikowi na naciśnięcie klawisza skrótu i uzyskanie pomocy na temat tego polecenia.

W przypadku określonego przesunięcia lub akcje, biorąc umieścić w `PreTranslateMessage` funkcja, która nie powinny mieć miejsce w trybie SHIFT + F1 Pomoc należy sprawdzić *m_bHelpMode* członkiem `CWinApp` przed wykonaniem tych instrukcji operacje. `CDialog` Implementacji `PreTranslateMessage` sprawdza to przed wywołaniem `IsDialogMessage`, na przykład. Powoduje to wyłączenie kluczy "okno dialogowe navigation" na Niemodalne okna dialogowe w trybie SHIFT + F1. Ponadto `CWinApp::OnIdle` nadal jest wywoływana podczas tej pętli.

Jeśli użytkownik wybierze polecenie menu, jest on traktowany jak uzyskać pomoc dotyczącą tego polecenia (przy użyciu WM_COMMANDHELP, zobacz poniżej). Jeśli użytkownik kliknie widoczne obszar okna aplikacji, jest wybierana jego jest w nieklienckim lub kliknij klienta. `OnContextHelp` Mapowanie uchwytów nieklienckim klika na kliknięcia klienta automatycznie. Jeśli kliknięcie klienta, następnie przesyła WM_HELPHITTEST do okna, który został kliknięty. Jeśli to okno zwraca wartość różną od zera, ta wartość służy jako kontekst pomocy. Jeśli zostanie zwrócona wartość zero, `OnContextHelp` próbuje okna nadrzędnego (i kończy się niepowodzeniem, jego element nadrzędny i tak dalej). Jeśli nie można ustalić kontekstu pomocy, wartością domyślną jest wysyłać polecenia id_default_help — okno główne, która jest następnie (zazwyczaj) mapowana `CWinApp::OnHelpIndex`.

## <a name="wmhelphittest"></a>WM_HELPHITTEST

```

afx_msg LRESULT CWnd::OnHelpHitTest(
WPARAM, LPARAM lParam)
```

WM_HELPHITTEST jest MFC prywatnej windows komunikat o błędzie jest odbierany przez aktywne okno kliknięto w trybie SHIFT + F1 Pomoc. Gdy okno odbiera ten komunikat, zwraca **DWORD** identyfikator pomocy na potrzeby używania przez WinHelp.

LOWORD(lParam) zawiera współrzędne urządzenia osi x, gdzie kliknięcia myszy względem pola klienta okna.

HIWORD(lParam) zawiera współrzędną y.

*wParam*<br/>
Nie jest używana i będzie mieć wartość zero. Jeśli wartość zwracana jest wartość różną od zera, WinHelp jest wywoływana z tego kontekstu. Jeśli wartość zwracana wynosi zero, okno nadrzędne jest wysyłane zapytanie w celu uzyskania pomocy.

W wielu przypadkach można skorzystać z testowania trafień kodu, który może już istnieć. Zobaczyć wdrożenia `CToolBar::OnHelpHitTest` przykładem obsługi komunikatu WM_HELPHITTEST (kod wykorzystuje kod testowania trafienia używany dla przycisków i etykietek narzędzi w `CControlBar`).

## <a name="mfc-application-wizard-support-and-makehm"></a>Obsługa kreatora aplikacji MFC i MAKEHM

Kreator aplikacji MFC tworzy pliki niezbędne do tworzenia pliku pomocy (pliki .cnt i .hpj). Obejmuje również liczbę plików wbudowane .rtf, które są akceptowane przez kompilator pomocy firmy Microsoft. Wiele tematów są kompletne, ale niektóre mogą wymagać modyfikacji dla określonych aplikacji.

Automatyczne tworzenie pliku "help mapowania" jest obsługiwany przez narzędzie MAKEHM wywoływana. Narzędzie MAKEHM można tłumaczyć zasobów aplikacji. Plik H do pliku mapowania pomocy. Na przykład:

```
#define IDD_MY_DIALOG   2000
#define ID_MY_COMMAND   150
```

zostanie zamieniona na:

```
HIDD_MY_DIALOG    0x207d0
HID_MY_COMMAND    0x10096
```

Ten format jest zgodny z kompilatora plików pomocy funkcji, który mapuje identyfikatory kontekstu (cyfr po prawej stronie) przy użyciu nazwy tematów (symbole po lewej stronie).

Kod źródłowy MAKEHM jest dostępna w przykładzie narzędzia do programowania MFC [MAKEHM](../visual-cpp-samples.md).

## <a name="adding-help-support-after-running-the-mfc-application-wizard"></a>Dodanie obsługi pomocy po uruchomieniu Kreatora aplikacji MFC

Najlepszym sposobem dodania pomocy w aplikacji jest zaznacz opcję "Context-sensitive Help", na stronie funkcje zaawansowane w Kreatorze aplikacji MFC przed utworzeniem aplikacji. W ten sposób Kreator aplikacji MFC automatycznie dodaje wpisy mapy komunikatów niezbędne do Twojej `CWinApp`-klasy do obsługi pomocy.

## <a name="help-on-message-boxes"></a>Pomoc na temat okna komunikatów

Pomoc dotyczącą okna komunikatów (nazywane również alerty) jest świadczona za pośrednictwem `AfxMessageBox` funkcji, otokę dla `MessageBox` interfejsu Windows API.

Istnieją dwie wersje `AfxMessageBox`, jeden do użycia z usługą identyfikator ciągu, a drugi do użycia ze wskaźnikiem do ciągu (`LPCSTR`):

```
int AFXAPI AfxMessageBox(LPCSTR lpszText,
    UINT nType,
    UINT nIDHelp);

int AFXAPI AfxMessageBox(UINT nIDPrompt,
    UINT nType,
    UINT nIDHelp);
```

W obu przypadkach jest opcjonalna Pomoc identyfikatora.

W pierwszym przypadku nIDHelp wartość domyślna to 0, co oznacza brak pomocy dla tego okna komunikatu. Jeśli użytkownik naciśnie klawisz F1, np. komunikat o okno jest aktywne, użytkownik nie otrzyma pomocy (nawet jeśli aplikacja obsługuje pomocy). Jeśli nie jest to pożądane, Identyfikatora pomocy należy podać nIDHelp.

W drugim przypadku wartość domyślną dla nIDHelp jest -1, która wskazuje, że identyfikator pomocy jest taka sama jak nIDPrompt. Pomoc będzie działać tylko wtedy, gdy aplikacja jest włączona pomoc oczywiście). Powinny zapewnić 0 nIDHelp, jeśli chcesz, że okno komunikatu ma nie pomoc techniczna. Powinien być komunikat, który ma być włączone, pomoc, ale pozwalają identyfikator pomocy innego niż nIDPrompt, po prostu Podaj dodatnią wartość nIDHelp innym niż nIDPrompt.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
