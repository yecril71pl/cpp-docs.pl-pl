---
title: 'TN028: obsługa pomocy kontekstowej'
ms.date: 11/04/2016
f1_keywords:
- vc.help
helpviewer_keywords:
- context-sensitive Help [MFC], MFC applications
- TN028
- resource identifiers, context-sensitive Help
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
ms.openlocfilehash: 502edc837d7886dd60ab5107fb194c1490a76928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370331"
---
# <a name="tn028-context-sensitive-help-support"></a>TN028: obsługa pomocy kontekstowej

W tej notatce opisano reguły przypisywania identyfikatorów kontekstów Pomocy i innych problemów z pomocą w MFC. Obsługa pomocy kontekstowej wymaga kompilatora pomocy, który jest dostępny w języku Visual C++.

> [!NOTE]
> Oprócz implementowania pomocy kontekstowej przy użyciu winhelp, MFC obsługuje również przy użyciu Pomocy HTML. Aby uzyskać więcej informacji na temat tej pomocy technicznej i programowania za pomocą Pomocy HTML, zobacz [Pomoc HTML: Kontekstowa pomoc dotycząca programów](../mfc/html-help-context-sensitive-help-for-your-programs.md).

## <a name="types-of-help-supported"></a>Rodzaje pomocy obsługiwane

Istnieją dwa typy pomocy kontekstowej zaimplementowane w aplikacjach systemu Windows. Pierwszy, o których mowa w "F1 Help" obejmuje uruchomienie WinHelp z odpowiednim kontekstem na podstawie aktualnie aktywnego obiektu. Drugi to tryb "Shift+ F1". W tym trybie kursor myszy zmienia się w kursor pomocy, a użytkownik przechodzi do kliknięcia obiektu. W tym momencie, WinHelp jest uruchamiany, aby udzielić pomocy dla obiektu, który użytkownik kliknął.

Klasy Microsoft Foundation implementują obie te formy pomocy. Ponadto struktura obsługuje dwa proste polecenia pomocy, Indeks Pomocy i Korzystanie z Pomocy.

## <a name="help-files"></a>Pliki pomocy

Klasy programu Microsoft Foundation zakładają jeden plik Pomocy. Ten plik Pomocy musi mieć taką samą nazwę i ścieżkę jak aplikacja. Na przykład, jeśli plikiem wykonywalnym jest C:\MyApplication\MyHelp.exe, plik pomocy musi być C:\MyApplication\MyHelp.hlp. Można ustawić ścieżkę przez *zmienną m_pszHelpFilePath* elementu członkowskiego [klasy CWinApp](../mfc/reference/cwinapp-class.md).

## <a name="help-context-ranges"></a>Zakresy kontekstów pomocy

Domyślna implementacja MFC wymaga, aby program przestrzegał niektórych reguł dotyczących przypisywania identyfikatorów kontekstu Pomocy. Reguły te są zakres identyfikatorów przydzielonych do określonych formantów. Można zastąpić te reguły, zapewniając różne implementacje różnych funkcji członkowskich związanych z Pomocą.

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

## <a name="simple-help-commands"></a>Proste polecenia "Pomoc"

Istnieją dwa proste polecenia Pomocy, które są implementowane przez Microsoft Foundation Classes:

- ID_HELP_INDEX który jest realizowany przez [CWinApp::OnHelpIndex](../mfc/reference/cwinapp-class.md#onhelpindex)

- ID_HELP_USING który jest implementowany przez [CWinApp::OnHelpUsing](../mfc/reference/cwinapp-class.md#onhelpusing)

Pierwsze polecenie pokazuje indeks Pomocy dla aplikacji. Drugi pokazuje pomoc użytkownika przy użyciu programu WinHelp.

## <a name="context-sensitive-help-f1-help"></a>Pomoc kontekstowa (Pomoc F1)

Klawisz F1 jest zwykle tłumaczony na polecenie o identyfikatorze ID_HELP przez akcelerator umieszczony w tabeli akceleratora głównego okna. Polecenie ID_HELP może być również generowane przez przycisk o identyfikatorze ID_HELP w oknie głównym lub oknie dialogowym.

Niezależnie od sposobu generowania polecenia ID_HELP jest ono kierowane jako zwykłe polecenie, dopóki nie osiągnie programu obsługi poleceń. Więcej informacji na temat architektury routingu poleceń MFC można znaleźć w [notatce technicznej 21](../mfc/tn021-command-and-message-routing.md). Jeśli aplikacja ma włączoną Pomoc, polecenie ID_HELP będzie obsługiwane przez [CWinApp::OnHelp](../mfc/reference/cwinapp-class.md#onhelp). Obiekt aplikacji odbiera komunikat pomocy, a następnie kieruje polecenie odpowiednio. Jest to konieczne, ponieważ domyślne routing polecenia nie jest odpowiedni do określenia najbardziej określonego kontekstu.

`CWinApp::OnHelp`próbuje uruchomić WinHelp w następującej kolejności:

1. Sprawdza, czy `AfxMessageBox` aktywne połączenie ma identyfikator pomocy. Jeśli okno komunikatu jest aktualnie aktywne, program WinHelp jest uruchamiany z kontekstem odpowiednim dla tego okna komunikatu.

1. Wysyła wiadomość WM_COMMANDHELP do aktywnego okna. Jeśli to okno nie odpowiada przez uruchomienie WinHelp, ten sam komunikat jest następnie wysyłany do przodków tego okna, dopóki wiadomość jest przetwarzana lub bieżące okno jest oknem najwyższego poziomu.

1. Wysyła polecenie ID_DEFAULT_HELP do okna głównego. Wywołuje to domyślną Pomoc. To polecenie jest zazwyczaj `CWinApp::OnHelpIndex`mapowane na .

Aby globalnie zastąpić domyślne wartości bazowe identyfikatora (np. 0x10000 dla poleceń i 0x20000 dla zasobów, takich jak okna dialogowe), aplikacja powinna zastąpić [CWinApp::WinHelp](../mfc/reference/cwinapp-class.md#winhelp).

Aby zastąpić tę funkcję i sposób, w jaki kontekst Pomocy jest określany, należy obsłużyć komunikat WM_COMMANDHELP. Możesz podać bardziej szczegółowe routing pomocy niż zapewnia struktura, ponieważ tylko idzie tak głęboko, jak bieżące okno podrzędne MDI. Można również zapewnić bardziej szczegółową pomoc dla określonego okna lub okna dialogowego, być może na podstawie bieżącego stanu wewnętrznego tego obiektu lub aktywnego formantu w oknie dialogowym.

## <a name="wm_commandhelp"></a>WM_COMMANDHELP

```

afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)
```

WM_COMMANDHELP jest prywatną wiadomością MFC systemu Windows, która jest odbierana przez aktywne okno, gdy jest wymagane Pomoc. Gdy okno odbiera ten komunikat, `CWinApp::WinHelp` może wywołać z kontekstu, który pasuje do stanu wewnętrznego okna.

*Lparam*<br/>
Zawiera aktualnie dostępny kontekst Pomocy. *lParam* wynosi zero, jeśli nie określono kontekstu Pomocy. Implementacja `OnCommandHelp` można użyć identyfikatora kontekstu w *lParam,* aby określić `CWinApp::WinHelp`inny kontekst lub można po prostu przekazać go do .

*Wparam*<br/>
Nie jest używany i będzie zero.

Jeśli `OnCommandHelp` funkcja `CWinApp::WinHelp`wywołuje , należy zwrócić **TRUE**. Zwracanie **funkcji TRUE** powoduje zatrzymanie routingu tego polecenia do innych klas i do innych okien.

## <a name="help-mode-shiftf1-help"></a>Tryb pomocy (Pomoc Shift+F1)

Jest to druga forma pomocy kontekstowej. Ogólnie rzecz biorąc, ten tryb jest wprowadzany przez naciśnięcie klawiszy SHIFT + F1 lub za pomocą menu / paska narzędzi. Jest on implementowany jako polecenie (ID_CONTEXT_HELP). Hak filtru wiadomości nie jest używany do tłumaczenia tego polecenia, gdy modalne okno dialogowe lub menu jest aktywne, dlatego`CWinApp::Run`to polecenie jest dostępne tylko dla użytkownika, gdy aplikacja wykonuje pompę wiadomości głównej ( ).

Po przejściu w ten tryb kursor myszy Pomocy jest wyświetlany we wszystkich obszarach aplikacji, nawet jeśli aplikacja normalnie wyświetlałaby własny kursor dla tego obszaru (na przykład obramowanie rozmiaru wokół okna). Użytkownik może wybrać polecenie za pomocą myszy lub klawiatury. Zamiast wykonywać polecenie, wyświetlana jest pomoc w tym poleceniu. Ponadto użytkownik może kliknąć widoczny obiekt na ekranie, taki jak przycisk na pasku narzędzi, a Pomoc zostanie wyświetlona dla tego obiektu. Ten tryb Pomocy jest `CWinApp::OnContextHelp`dostarczany przez plik .

Podczas wykonywania tej pętli wszystkie dane wejściowe klawiatury są nieaktywne, z wyjątkiem klawiszy, które uzyskują dostęp do menu. Ponadto tłumaczenie polecenia jest `PreTranslateMessage` nadal wykonywane za pomocą, aby umożliwić użytkownikowi naciśnięcie klawisza akceleratora i otrzymanie pomocy w tym poleceniu.

Jeśli istnieją określone tłumaczenia lub akcje `PreTranslateMessage` odbywające się w funkcji, które nie powinny mieć miejsce w trybie `CWinApp` pomocy SHIFT + F1, należy sprawdzić *m_bHelpMode* członka przed wykonaniem tych operacji. Wdrożenie `CDialog` `PreTranslateMessage` sprawdza to przed `IsDialogMessage`wywołaniem , na przykład. Spowoduje to wyłączenie klawiszy "nawigacji w oknie dialogowym" w niemodytnych oknach dialogowych w trybie SHIFT+F1. Ponadto nadal `CWinApp::OnIdle` jest wywoływana podczas tej pętli.

Jeśli użytkownik wybierze polecenie z menu, jest ono traktowane jako pomoc w tym poleceniu (za pośrednictwem WM_COMMANDHELP, patrz poniżej). Jeśli użytkownik kliknie widoczny obszar okna aplikacji, zostanie dokonane określenie, czy jest to kliknięcie nieklukowe, czy kliknięcie klienta. `OnContextHelp`automatycznie obsługuje mapowanie kliknięć nieklientów do kliknięć klienta. Jeśli jest to kliknięcie klienta, następnie wysyła WM_HELPHITTEST do okna, które zostało kliknięte. Jeśli to okno zwraca wartość niezerową, ta wartość jest używana jako kontekst pomocy. Jeśli zwraca zero, `OnContextHelp` próbuje okna nadrzędnego (i w przypadku niepowodzenia, jego nadrzędnego i tak dalej). Jeśli nie można określić kontekstu Pomocy, domyślnie należy wysłać polecenie ID_DEFAULT_HELP do okna głównego, `CWinApp::OnHelpIndex`które jest (zwykle) mapowane na .

## <a name="wm_helphittest"></a>WM_HELPHITTEST

```

afx_msg LRESULT CWnd::OnHelpHitTest(
WPARAM, LPARAM lParam)
```

WM_HELPHITTEST jest komunikatem systemu Windows dla systemu windows owego MFC, który jest odbierany przez aktywne okno kliknięte podczas trybu pomocy SHIFT+F1. Gdy okno odbiera ten komunikat, zwraca identyfikator pomocy **DWORD** do użycia przez WinHelp.

LOWORD(lParam) zawiera współrzędną urządzenia osi X, w której kliknięto mysz względem obszaru klienta okna.

HIWORD(lParam) zawiera współrzędną osi Y.

*Wparam*<br/>
nie jest używany i będzie zerowy. Jeśli zwracana wartość jest niezerowa, WinHelp jest wywoływana z tym kontekstem. Jeśli zwracana wartość wynosi zero, okno nadrzędne jest wyszukiwane o pomoc.

W wielu przypadkach możesz wykorzystać kod testowania trafień, który może już mieć. Zobacz implementację `CToolBar::OnHelpHitTest` na przykład obsługi wiadomości WM_HELPHITTEST (kod wykorzystuje kod testu trafień używany na przyciskach `CControlBar`i etykietkach narzędzi w ).

## <a name="mfc-application-wizard-support-and-makehm"></a>Obsługa kreatora aplikacji MFC i MAKEHM

Kreator aplikacji MFC tworzy pliki niezbędne do utworzenia pliku Pomocy (.cnt i .hpj). Zawiera również szereg wstępnie utworzonych plików .rtf, które są akceptowane przez kompilator pomocy firmy Microsoft. Wiele tematów są kompletne, ale niektóre mogą wymagać zmodyfikowane dla określonej aplikacji.

Automatyczne tworzenie pliku "mapowanie pomocy" jest obsługiwane przez narzędzie o nazwie MAKEHM. Narzędzie MAKEHM może przetłumaczyć zasób aplikacji. H do pliku mapowania Pomocy. Przykład:

```
#define IDD_MY_DIALOG   2000
#define ID_MY_COMMAND   150
```

zostaną przetłumaczone na:

```
HIDD_MY_DIALOG    0x207d0
HID_MY_COMMAND    0x10096
```

Ten format jest zgodny z funkcją kompilatora Pomocy, która mapuje identyfikatory kontekstu (liczby po prawej stronie) z nazwami tematów (symbolami po lewej stronie).

Kod źródłowy MAKEHM jest dostępny w przykładzie MFC Programming Utilities [MAKEHM](../overview/visual-cpp-samples.md).

## <a name="adding-help-support-after-running-the-mfc-application-wizard"></a>Dodawanie pomocy technicznej po uruchomieniu Kreatora aplikacji MFC

Najlepszym sposobem dodania Pomocy do aplikacji jest sprawdzenie opcji "Pomoc kontekstowa" na stronie Funkcje zaawansowane Kreatora aplikacji MFC przed utworzeniem aplikacji. W ten sposób Kreator aplikacji MFC automatycznie dodaje niezbędne `CWinApp`wpisy mapy komunikatów do klasy pochodnej do obsługi Pomocy.

## <a name="help-on-message-boxes"></a>Pomoc dotycząca skrzynek wiadomości

Pomoc w oknach komunikatów (czasami nazywane `AfxMessageBox` alertami) jest `MessageBox` obsługiwana za pośrednictwem funkcji, otoki interfejsu API systemu Windows.

Istnieją dwie wersje `AfxMessageBox`, jedna do użycia z identyfikatorem ciągu, a`LPCSTR`druga do użycia ze wskaźnikiem do ciągu ( ):

```
int AFXAPI AfxMessageBox(LPCSTR lpszText,
    UINT nType,
    UINT nIDHelp);

int AFXAPI AfxMessageBox(UINT nIDPrompt,
    UINT nType,
    UINT nIDHelp);
```

W obu przypadkach istnieje opcjonalny identyfikator pomocy.

W pierwszym przypadku wartość domyślna dla nIDHelp wynosi 0, co oznacza brak Pomocy dla tego okna komunikatu. Jeśli użytkownik naciśnie klawisz F1, gdy jest aktywne, użytkownik nie otrzyma Pomocy (nawet jeśli aplikacja obsługuje Pomoc). Jeśli nie jest to pożądane, identyfikator pomocy powinien być podany dla nIDHelp.

W drugim przypadku wartość domyślna dla nIDHelp wynosi -1, co oznacza, że identyfikator pomocy jest taki sam jak nIDPrompt. Pomoc będzie działać tylko wtedy, gdy aplikacja jest pomoc-enabled, oczywiście). Należy podać 0 dla nIDHelp, jeśli chcesz, aby okno komunikatu nie było pomocne. Jeśli chcesz, aby wiadomość była Pomoc włączona, ale pragnienie innego identyfikatora pomocy niż nIDPrompt, po prostu podać wartość dodatnią dla nIDHelp różni się od nIDPrompt.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
