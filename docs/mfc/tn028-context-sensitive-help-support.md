---
title: 'TN028: Obsługa pomocy kontekstowej | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.help
dev_langs:
- C++
helpviewer_keywords:
- context-sensitive Help [MFC], MFC applications
- TN028
- resource identifiers, context-sensitive Help
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 58caed14e6b7080405cceb30cfb90623d28dc83e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tn028-context-sensitive-help-support"></a>TN028: obsługa pomocy kontekstowej
Ta uwaga przedstawiono zasady przypisywania identyfikatorów kontekstów pomocy i inne problemy pomocy w MFC. Obsługa pomocy kontekstowej wymaga pomocy kompilatora, która jest dostępna w programie Visual C++.  
  
> [!NOTE]
>  Oprócz wykonania pomocy kontekstowej przy użyciu WinHelp, MFC umożliwia korzystanie z pomocy HTML. Aby uzyskać więcej informacji na tej obsługę programowania w języku pomocy HTML, zobacz [Pomoc HTML: Context-Sensitive Pomoc dla programów Your](../mfc/html-help-context-sensitive-help-for-your-programs.md).  
  
## <a name="types-of-help-supported"></a>Typy obsługiwane pomocy  
 Istnieją dwa rodzaje pomocy kontekstowej zaimplementowane w aplikacjach systemu Windows. Pierwsza strona, określane jako "Pomocy F1" obejmuje uruchamianie WinHelp z odpowiedniego kontekstu oparte na aktualnie aktywnego obiektu. Drugim jest tryb "Shift + F1". W tym trybie kursor zmienia się na kursor pomocy, a użytkownik przechodzi do kliknij obiekt. W tym momencie WinHelp jest uruchamiana, aby uzyskać pomoc dla obiekt, który użytkownik kliknął.  
  
 Biblioteka Microsoft Foundation Classes implementuje obu formach pomocy. Ponadto platforma obsługuje dwa polecenia pomocy prostego indeksu Pomocy i korzystanie z pomocy.  
  
## <a name="help-files"></a>Pliki pomocy  
 Microsoft Foundation classes założono pojedynczego pliku pomocy. Ten plik pomocy musi mieć taką samą nazwę i ścieżkę, co aplikacja. Na przykład jeśli plik wykonywalny jest C:\MyApplication\MyHelp.exe plik pomocy musi być C:\MyApplication\MyHelp.hlp. Ustaw ścieżkę za pośrednictwem `m_pszHelpFilePath` zmiennej członkowskiej z [cwinapp — klasa](../mfc/reference/cwinapp-class.md).  
  
## <a name="help-context-ranges"></a>Zakresy kontekstu pomocy  
 Domyślna implementacja MFC wymaga programu do wykonania niektórych reguł o przypisywaniu kontekstu pomocy identyfikatorów. Te reguły są zakres identyfikatorów przydzielone do kontrolek. Te reguły można zastąpić, zapewniając różnych implementacji różnych funkcji Członkowskich związanych z pomocy.  
  
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
  
## <a name="simple-help-commands"></a>Polecenia proste "Help"  
 Istnieją dwa proste implementowane przez Microsoft Foundation Classes polecenia pomocy:  
  
-   Id_help_index —, która jest zaimplementowana przez [CWinApp::OnHelpIndex](../mfc/reference/cwinapp-class.md#onhelpindex)  
  
-   Id_help_using —, która jest zaimplementowana przez [CWinApp::OnHelpUsing](../mfc/reference/cwinapp-class.md#onhelpusing)  
  
 Pierwsze polecenie zawiera indeks pomocy dla aplikacji. Drugi zawiera pomocy użytkownika za pomocą programu WinHelp.  
  
## <a name="context-sensitive-help-f1-help"></a>Pomoc kontekstowa (pomocy F1)  
 Klawisz F1 jest zwykle translacji polecenia o identyfikatorze `ID_HELP` przez akceleratora umieszczone w tabeli akceleratora głównego okna. `ID_HELP` Polecenie może być również generowany przez przycisk o identyfikatorze `ID_HELP` na główne okno lub okno dialogowe.  
  
 Niezależnie od tego, jak `ID_HELP` polecenia jest generowany, dopóki nie osiągnie programem obsługi jest kierowany jako normalne polecenia. Aby uzyskać więcej informacji o architekturze routing poleceń MFC, zapoznaj się [techniczne notatkę 21](../mfc/tn021-command-and-message-routing.md). Jeśli aplikacja ma włączone, pomocy `ID_HELP` polecenia będzie obsługiwany przez [CWinApp::OnHelp](../mfc/reference/cwinapp-class.md#onhelp). Obiekt aplikacji otrzymuje komunikat pomocy, a następnie przekierowuje odpowiednio polecenia. Jest to konieczne, ponieważ domyślny routing poleceń nie są wystarczające do określenia najbardziej specyficznego kontekstu.  
  
 `CWinApp::OnHelp` próbuje uruchomić WinHelp w następującej kolejności:  
  
1.  Sprawdza, czy aktywny `AfxMessageBox` wywołać przy użyciu identyfikatora pomocy. Jeśli okno komunikatu jest obecnie aktywny, WinHelp jest uruchamiane w kontekście należy to okno.  
  
2.  Wysyła komunikat WM_COMMANDHELP aktywnego okna. Jeśli okno nie odpowiada za uruchamianie WinHelp, ten sam komunikat jest następnie wysyłane do nadrzędne tego okna, dopóki komunikat jest przetwarzany lub bieżące okno jest oknem najwyższego poziomu.  
  
3.  Wysyła polecenie id_default_help — do głównego okna. Wywołuje to domyślna Pomoc. To polecenie jest zwykle mapowane na `CWinApp::OnHelpIndex`.  
  
 Aby zastąpić globalny identyfikator podstawowej wartości domyślne (np. 0x10000 dla poleceń i 0x20000 dla zasobów, takich jak wyświetlanie okien dialogowych), aplikacji powinny zastępować [CWinApp::WinHelp](../mfc/reference/cwinapp-class.md#winhelp).  
  
 Aby zastąpić tę funkcję i sposób ustalona kontekstu pomocy, powinna obsługiwać komunikatu WM_COMMANDHELP. Możesz przeprowadzić bardziej szczegółowe pomocy routing niż zapewnia platformę, ponieważ tylko przechodzi ona głębokość jako bieżącego okna podrzędnego MDI. Można również do zapewnienia dokładniejszych pomocy okno lub okna dialogowego, prawdopodobnie na podstawie bieżącego wewnętrznego stanu tego obiektu lub aktywnego formantu w oknie dialogowym.  
  
## <a name="wmcommandhelp"></a>WM_COMMANDHELP  
  
```  
 
afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)  
 
```  
  
 WM_COMMANDHELP jest prywatne Windows MFC komunikat jest odbierany przez aktywnego okna, gdy pomoc zostanie wywołana. Gdy okno odbiera ten komunikat, może ono wywołać metodę `CWinApp::WinHelp` z kontekstem zgodny stan wewnętrzny okna.  
  
 `lParam`  
 Zawiera obecnie kontekstu pomocy. `lParam` wynosi zero, jeśli nie zostały stwierdził brak kontekstu pomocy. Implementacja interfejsu `OnCommandHelp` można użyć Identyfikatora kontekstu w `lParam` można określić różne kontekstu lub można po prostu przekaż go do `CWinApp::WinHelp`.  
  
 `wParam`  
 Nie jest używany i będą miały wartość zero.  
  
 Jeśli `OnCommandHelp` wywołania funkcji `CWinApp::WinHelp`, powinien on zwrócić `TRUE`. Zwracanie `TRUE` zatrzymuje routingu tego polecenia do innych klas i inne systemu windows.  
  
## <a name="help-mode-shiftf1-help"></a>Tryb pomocy (Pomoc Shift + F1)  
 Jest to drugiej formy pomoc kontekstową. Ogólnie rzecz biorąc w tym trybie jest wprowadzana przez naciśnięcie klawisza SHIFT + F1 lub za pośrednictwem menu/pasek narzędzi. Są one zaimplementowane jako polecenia (**id_context_help —**). Haku filtr komunikatu nie jest używany do tłumaczenia to polecenie podczas modalne okno dialogowe lub menu jest aktywna, dlatego to polecenie jest dostępne tylko dla użytkownika przy aplikacji jest wykonywany pompa głównej wiadomości (`CWinApp::Run`).  
  
 Po wprowadzeniu ten tryb, kursor myszy pomocy jest wyświetlany na wszystkie obszary aplikacji, nawet w przypadku aplikacji zwykle wyświetla własną kursor dla tego obszaru (na przykład zmiany rozmiaru obramowanie okna). Użytkownik będzie mógł wybierz polecenie za pomocą myszy lub klawiatury. Zamiast wykonywania polecenia, zostanie wyświetlony pomoc na temat tego polecenia. Ponadto użytkownik może kliknąć obiekt widoczne na ekranie, takie jak przycisk na pasku zadań i będzie można wyświetlić pomocy dla tego obiektu. Ten rodzaj pomocy jest zapewniana przez `CWinApp::OnContextHelp`.  
  
 Podczas wykonywania tej pętli klawiatury wszystkich danych wejściowych jest nieaktywny, z wyjątkiem klucze, które uzyskują dostęp do menu. Ponadto tłumaczenia polecenie jest nadal wykonywane za pośrednictwem `PreTranslateMessage` umożliwia użytkownikom naciśnięcie klawisza skrótu i uzyskać pomoc dotyczącą tego polecenia.  
  
 W przypadku konkretnego translacji lub akcje biorąc umieścić w `PreTranslateMessage` funkcji, które nie powinny mieć miejsce w trybie SHIFT + F1 Pomoc, należy sprawdzić `m_bHelpMode` członkiem `CWinApp` przed wykonaniem tych operacji. `CDialog` Implementacja `PreTranslateMessage` sprawdza to przed wywołaniem `IsDialogMessage`, np. Powoduje wyłączenie kluczy "nawigacji okna dialogowego" na Niemodalne okna dialogowe w trybie SHIFT + F1. Ponadto `CWinApp::OnIdle` nadal jest wywoływana podczas tej pętli.  
  
 Jeśli użytkownik wybierze polecenie menu, jest on traktowany jak uzyskać pomoc dotyczącą tego polecenia (za pośrednictwem **WM_COMMANDHELP**, patrz poniżej). Gdy użytkownik kliknie widoczny obszar okna aplikacji, jest wybierana określające, czy jest nieklienckim lub kliknij klienta. `OnContextHelp` Mapowanie uchwytów nieklienckim kliknie automatycznie kliknięć klienta. Jeśli jest kliknij klienta, następnie wysyła **WM_HELPHITTEST** do okna, który został kliknięty. Jeśli okno zwróci wartość niezerową, ta wartość służy jako kontekst Aby uzyskać pomoc. Jeśli zmienna zwraca zero, `OnContextHelp` próbuje okno nadrzędne (i awarii, który nadrzędnego i tak dalej). Jeśli nie można ustalić kontekstu pomocy, wartością domyślną jest wysłać **id_default_help —** polecenia do głównego okna, która następnie (zwykle) jest mapowana na `CWinApp::OnHelpIndex`.  
  
## <a name="wmhelphittest"></a>WM_HELPHITTEST  
  
```  
 
afx_msg LRESULT CWnd::OnHelpHitTest(
WPARAM, LPARAM lParam)  
```  
  
 **WM_HELPHITTEST** jest MFC windows prywatnej komunikat o błędzie jest odbierany przez aktywne okno kliknięty w trybie SHIFT + F1 Pomoc. Gdy okno odbiera ten komunikat, zwraca identyfikator pomocy DWORD do użycia przy pomocy systemu Windows.  
  
 LOWORD(lParam)  
 zawiera współrzędnych urządzenia osi x, gdy wskaźnik myszy został kliknięty względem obszaru klienckiego okna.  
  
 HIWORD(lParam)  
 zawiera współrzędną y.  
  
 `wParam`  
 Nie jest używany i będą miały wartość zero. Jeśli wartość zwracana jest niezerowa, WinHelp jest wywoływana z tym kontekstem. Jeśli wartość zwracana jest wartość zero, aby uzyskać pomoc jest poddawany kwerendzie okno nadrzędne.  
  
 W wielu przypadkach można wykorzystać testowania trafień kodu, który może już istnieć. Zobaczyć realizacji **CToolBar::OnHelpHitTest** przykład obsługa **WM_HELPHITTEST** wiadomości (kod wykorzystuje kod testu trafień używany dla przycisków i etykietki narzędzi w `CControlBar`).  
  
## <a name="mfc-application-wizard-support-and-makehm"></a>Obsługa kreatora aplikacji MFC i MAKEHM  
 Kreator aplikacji MFC tworzy pliki niezbędne do utworzenia pliku pomocy (pliki .cnt i .hpj). Zawiera także wiele plików RTF wbudowane, które są akceptowane przez kompilator pomocy firmy Microsoft. Wiele tematów zostaną ukończone, ale niektóre może zajść potrzeba jego zmodyfikowania dla konkretnej aplikacji.  
  
 Automatyczne tworzenie pliku "help mapowania" jest obsługiwana przez narzędzie MAKEHM wywołana. Narzędzie MAKEHM może dokonywać translacji zasobów aplikacji. Plik H do mapowania pliku pomocy. Na przykład:  
  
```  
#define IDD_MY_DIALOG   2000  
#define ID_MY_COMMAND   150  
```  
  
 zostanie zamieniona na:  
  
```  
HIDD_MY_DIALOG    0x207d0  
HID_MY_COMMAND    0x10096  
```  
  
 Ten format jest zgodny, za pomocą pomocy kompilatora, która mapuje identyfikatorów kontekstu (cyfry po prawej stronie) z nazwami tematu (symboli po lewej stronie).  
  
 Kod źródłowy MAKEHM jest dostępna w przykładzie narzędzia do programowania MFC [MAKEHM](../visual-cpp-samples.md).  
  
## <a name="adding-help-support-after-running-the-mfc-application-wizard"></a>Dodawanie obsługi pomocy po uruchomieniu Kreatora aplikacji MFC  
 Zaznacz opcję "Context-sensitive Help", na stronie funkcje zaawansowane, Kreator aplikacji MFC przed utworzeniem aplikacji jest najlepszy sposób, aby dodać Pomoc do tej aplikacji. W ten sposób Kreator aplikacji MFC automatycznie dodaje wpisy mapy wiadomości niezbędne do Twojej `CWinApp`-klasy do obsługi pomocy.  
  
## <a name="help-on-message-boxes"></a>Pomoc na temat pola komunikatów  
 Pomoc na temat pola wiadomości (nazywane również alerty) jest obsługiwana przez `AfxMessageBox` funkcji, otoki dla `MessageBox` interfejsu API systemu Windows.  
  
 Istnieją dwie wersje `AfxMessageBox`, jeden do użycia z identyfikator ciągu i jeden do użycia ze wskaźnikiem do ciągu (`LPCSTR`):  
  
```  
int AFXAPI AfxMessageBox(LPCSTR lpszText,
    UINT nType,
    UINT nIDHelp);

int AFXAPI AfxMessageBox(UINT nIDPrompt,
    UINT nType,
    UINT nIDHelp);
```  
  
 W obu przypadkach jest opcjonalny pomocy identyfikatora.  
  
 W pierwszym przypadku nIDHelp wartością domyślną jest 0, co oznacza brak pomocy dla tego okna komunikatu. Jeśli użytkownik naciśnie klawisz F1 podczas takie jak wiadomości okno jest aktywne, użytkownik nie otrzyma pomocy (nawet, jeśli aplikacja obsługuje pomocy). Jeśli nie jest to pożądane, Identyfikatora pomocy należy przewidzieć nIDHelp.  
  
 W drugim przypadku wartość domyślną nIDHelp jest -1, która wskazuje, że identyfikator pomocy jest taka sama jak nIDPrompt. Pomocy działa tylko wtedy, gdy aplikacja jest włączona pomoc oczywiście). 0 powinno zapewniać dla nIDHelp, jeśli chcesz, że okno komunikatu pomocy nie są obsługiwane. Należy ma komunikat, który ma być włączone, pomocy, ale konieczna jest identyfikator pomocy innego niż nIDPrompt, wystarczy podać wartość dodatnią dla nIDHelp innym niż nIDPrompt.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

