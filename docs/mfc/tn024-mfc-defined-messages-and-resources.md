---
title: 'TN024: Komunikaty i zasoby zdefiniowane przez MFC'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.messages
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 029177821d37d5d26abe0b39ea1581e8a5ad602b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306028"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024: Komunikaty i zasoby zdefiniowane przez MFC

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisuje komunikaty wewnętrzne Windows i formatów zasobów używane przez MFC. Tych informacji opisano wdrożenia RAM, a następnie pomoże Ci w debugowaniu aplikacji. Dla żądnemu nawet jeśli te informacje nie jest oficjalnie obsługiwany, można użyć niektóre z tych informacji dla implementacji zaawansowane.

Ta uwaga zawiera szczegółów implementacji prywatnej MFC; Cała zawartość mogą ulec zmianie w przyszłości. Wiadomości Windows MFC mają znaczenie w zakresie tylko jednej aplikacji, ale zmieni się w przyszłości na zawierają komunikaty całego systemu.

Wiadomości Windows prywatnych zakresu MFC i typów zasobów są w zakresie zastrzeżonych "system" wydzielone Microsoft Windows. Obecnie nie wszystkie liczby w zakresach są używane, a w przyszłości, można użyć nowych numerów w zakresie. Aktualnie używanego numery mogą ulec zmianie.

Windows prywatnej MFC, komunikaty są w zakresie 0x360 -> 0x37F.

MFC prywatnego zasobu, które typy znajdują się w zakresie 0xF0 -> 0xFF.

**Wiadomości Windows prywatne MFC**

Te komunikaty Windows są używane zamiast funkcji wirtualnych języka C++, w których jest wymagane stosunkowo luźne powiązanie między obiektami okien i gdy wirtualna funkcja C++ nie jest właściwe.

Te wiadomości Windows prywatnych i strukturami skojarzonego parametru są deklarowane w nagłówku prywatnej MFC "AFXPRIV. H ". Wyświetlane ostrzeżenie, znajdujących się w kodzie, który zawiera ten nagłówek może polegać na nieudokumentowane zachowanie i podziału prawdopodobnie będzie w przyszłości wersje biblioteki MFC.

Rzadkimi przypadkami o konieczności obsługiwać jeden z następujących komunikatów możesz użyć mapy wiadomości ON_MESSAGE — makro i obsłużyć komunikat ogólny format LRESULT/WPARAM/LPARAM.

**WM_QUERYAFXWNDPROC**

Ten komunikat jest wysyłany do okna, która jest tworzona. To jest wysyłany bardzo wczesnym etapie procesu tworzenia jako sposób określania, czy jest WndProc **AfxWndProc. AfxWndProc** zwraca wartość 1.

|||
|-|-|
|wParam|Nieużywane|
|lParam|Nieużywane|
|zwraca|1, jeśli przetwarzane przez **AfxWndProc**|

**WM_SIZEPARENT**

Ta wiadomość jest wysyłana przez okno ramek do jego bezpośrednie elementy podrzędne podczas zmiany rozmiaru (`CFrameWnd::OnSize` wywołania `CFrameWnd::RecalcLayout` która wywołuje metodę `CWnd::RepositionBars`) Aby zmienić położenie pasków sterowania całym rogu ramki. Struktura AFX_SIZEPARENTPARAMS zawiera bieżący prostokąt klienta dostępne nadrzędnej i HDWP, (która może być NULL) za pomocą którego można wywołać `DeferWindowPos` zminimalizować odświeżenie.

|||
|-|-|
|wParam|Nieużywane|
|lParam|Adres struktury AFX_SIZEPARENTPARAMS|
|zwraca|Nieużywane (0)|

Zignorowanie komunikatu wskazuje, czy okno nie uczestniczy w układzie.

**WM_SETMESSAGESTRING**

Ta wiadomość jest wysyłana do okna ramki poprosić, aby zaktualizować wiersz wiadomości w pasku stanu. Identyfikator ciągu lub LPCSTR może być określony (ale nie obu).

|||
|-|-|
|wParam|Ciąg Identyfikatora (lub zero)|
|lParam|LPCSTR ciągu (lub wartość NULL)|
|zwraca|Nieużywane (0)|

**WM_IDLEUPDATECMDUI**

Ta wiadomość jest wysyłana w czasie bezczynności do zaimplementowania Aktualizacja czasu bezczynności obsługi interfejsu użytkownika polecenia update. Jeśli okno (zazwyczaj pasek sterowania) obsługuje wiadomości, tworzy `CCmdUI` (lub obiektu klasy pochodnej) i wywołać `CCmdUI::DoUpdate` dla poszczególnych elementów"" w oknie. Z kolei spowoduje to zaewidencjonowanie ON_UPDATE_COMMAND_UI procedury obsługi dla obiektów w łańcuchu program obsługi poleceń.

|||
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|lParam|Nieużywane (0)|
|zwraca|Nieużywane (0)|

*bDisableIfNoHandler* jest różna od zera, można wyłączyć obiektu interfejsu użytkownika w przypadku nieprawidłowego ON_COMMAND ani ON_UPDATE_COMMAND_UI.

**WM_EXITHELPMODE**

Ta wiadomość zostanie opublikowana do `CFrameWnd` tryb, aby zakończyć działanie kontekstowej pomocy. Odebranie tej wiadomości kończy modalną pętlę uruchomione przez `CFrameWnd::OnContextHelp`.

|||
|-|-|
|wParam|Nieużywane (0)|
|lParam|Nieużywane (0)|
|zwraca|Nieużywane|

**WM_INITIALUPDATE**

Ta wiadomość jest wysyłana przez szablon dokumentu wszystkie elementy podrzędne okna ramki, gdy jest bezpieczne robić ich początkową aktualizacji. Jest on mapowany do wywołania `CView::OnInitialUpdate` , ale mogą być używane w innych `CWnd`-pochodnych klas dla innych jednorazowej aktualizacji.

|||
|-|-|
|wParam|Nieużywane (0)|
|lParam|Nieużywane (0)|
|zwraca|Nieużywane (0)|

**WM_RECALCPARENT**

Ta wiadomość jest wysyłana przez widok do okna nadrzędnego (uzyskane za pośrednictwem `GetParent`) aby wymusić ponowne obliczanie układu (zazwyczaj będzie wywoływać nadrzędnego `RecalcLayout`). Służy to w aplikacje serwera OLE gdzie jest to konieczne, dla ramki zwiększanie się rozmiaru, wraz ze wzrostem natężenia łączny rozmiar tego widoku.

Jeśli okno nadrzędne przetwarza ten komunikat powinien zwrócić wartość TRUE i wypełnić Prostokąt przekazanej lParam nowy rozmiar obszaru klienckiego. Jest on używany w `CScrollView` kiedy poprawnie obsłużyć paski przewijania (miejsce na zewnątrz okna, gdy zostaną one dodane) obiekt serwera jest aktywowany w miejscu.

|||
|-|-|
|wParam|Nieużywane (0)|
|lParam|RectClient lprect — może mieć wartości NULL|
|zwraca|Wartość TRUE, jeśli jest to nowy klient prostokąt zwrócone, wartość FALSE w przeciwnym razie|

**WM_SIZECHILD**

Ta wiadomość jest wysyłana przez `COleResizeBar` do okna właściciela (za pośrednictwem `GetOwner`) po użytkownik zmienia rozmiar pasek z uchwytami zmiany rozmiaru. `COleIPFrameWnd` odpowiada na tę wiadomość, próbując zmienić położenie okno ramowe, ponieważ użytkownik zgłosił żądanie.

Nowy prostokąt, podane we współrzędnych klienta względem ramki okna, który zawiera pasek zmiany rozmiaru jest wskazywanej przez lParam.

|||
|-|-|
|wParam|Nieużywane (0)|
|lParam|Lprect — rectNew|
|zwraca|Nieużywane (0)|

**WM_DISABLEMODAL**

Ta wiadomość jest wysyłana do wszystkich okien wyskakujących należące do ramki okna, które jest dezaktywowany. Na podstawie wyniku okno ramowe zdecydować, czy należy wyłączyć w oknie podręcznym.

Możesz użyć tego wykonać przetwarzana w specjalny sposób w oknie podręcznym, gdy ramka przechodzi do stanu modalnego lub zapobiec niektórych okien wyskakujących wyłączony. Etykietki narzędzi umożliwiają zniszczyć samodzielnie, gdy okno ramowe przechodzi w stan modalny, na przykład ten komunikat.

|||
|-|-|
|wParam|Nieużywane (0)|
|lParam|Nieużywane (0)|
|zwraca|Niezerowa Koniunkcja do **nie** wyłączaj okno, 0 oznacza, zostaną wyłączone okna|

**WM_FLOATSTATUS**

Ta wiadomość jest wysyłana do wszystkich okien wyskakujących własnością oknem ramki, gdy ramki jest aktywowany lub dezaktywowany przez inne okno ramek najwyższego poziomu. Jest on używany przez implementację MFS_SYNCACTIVE w `CMiniFrameWnd`, aby zachować synchronizację z aktywacji okno ramek najwyższego poziomu aktywacji tych okien wyskakujących.

|||
|-|-|
|wParam|Jest jednym z następujących wartości:<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|Nieużywane (0)|

Wartość zwracana powinna być różna od zera jeśli FS_SYNCACTIVE jest ustawiony, synchronizuje okna aktywacji za pomocą nadrzędnej ramki. `CMiniFrameWnd` Zwraca różna od zera, jeśli ustawiono MFS_SYNCACTIVE stylu.

Aby uzyskać więcej informacji, zobacz wykonania `CMiniFrameWnd`.

## <a name="wmactivatetoplevel"></a>WM_ACTIVATETOPLEVEL

Ten komunikat jest wysyłany do okien najwyższego poziomu, gdy okno w jego "najwyższego poziomu grupy" jest aktywowane lub dezaktywowane. Okno jest częścią grupy najwyższego poziomu jest oknem najwyższego poziomu (nie nadrzędnego lub właściciela), czy jest własnością okno programu. Ten komunikat jest podobnie jak WM_ACTIVATEAPP, ale działa w sytuacjach, w których należących do różnych procesów systemu windows mieszane w jednym oknie hierarchii (często używany w aplikacji OLE).

## <a name="wmcommandhelp-wmhelphittest-wmexithelpmode"></a>WM_EXITHELPMODE WM_COMMANDHELP, WM_HELPHITTEST,

Te komunikaty są używane w implementacji Pomoc kontekstowa. Zapoznaj się [Uwagi techniczne 28](../mfc/tn028-context-sensitive-help-support.md) Aby uzyskać więcej informacji.

## <a name="mfc-private-resource-formats"></a>Formatów zasobów prywatnych w MFC

Obecnie MFC definiuje dwa formaty prywatnego zasobu: Rt_toolbar — i RT_DLGINIT.

## <a name="rttoolbar-resource-format"></a>Rt_toolbar — zasób formatu

Pasek narzędzi domyślne, dostarczone przez AppWizard jest oparty na rt_toolbar — zasób niestandardowy, który został wprowadzony w MFC w wersji 4.0. Można edytować tego zasobu za pomocą paska narzędzi edytora.

## <a name="rtdlginit-resource-format"></a>Format zasobu RT_DLGINIT

Jednego formatu do prywatnego zasobu MFC jest używane do przechowywania informacji na temat inicjalizacji dodatkowe okna dialogowego. Obejmuje to ciągi początkowej, przechowywane w polu kombi. Format ten zasób nie jest przeznaczony do należy ręcznie edytować, ale są obsługiwane przez Visual C++.

Wizualne C++ i ten zasób RT_DLGINIT nie są wymagane do użycia powiązane funkcje MFC, ponieważ istnieją zamiast interfejsu API, korzystając z informacji w zasobie. Przy użyciu języka Visual C++ sprawia, że jest ona znacznie ułatwia pisanie, obsługa i tłumaczenie aplikację w perspektywie długoterminowej.

Podstawowa struktura zasobów RT_DLGINIT jest następująca:

```
+---------------+    \
| Control ID    |   UINT             |
+---------------+    |
| Message #     |   UINT             |
+---------------+    |
|length of data |   DWORD            |
+---------------+    |   Repeated
|   Data        |   Variable Length  |   for each control
|   ...         |   and Format       |   and message
+---------------+    /
|     0         |   BYTE
+---------------+
```

Powtórzony sekcja zawiera identyfikator formantu, który można wysłać komunikatu, komunikat # Wyślij (normalny komunikat Windows) i o zmiennej długości danych. Komunikat Windows są wysyłane w postaci:

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

Jest bardzo ogólny format, dzięki czemu wszystkie Windows wiadomości i zawartość danych. Edytor zasobów Visual C++ i MFC obsługują tylko ograniczonym podzbiorem Windows wiadomości: CB_ADDSTRING dla początkowych opcji lista dla pola kombi (dane to ciąg tekstowy).

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
