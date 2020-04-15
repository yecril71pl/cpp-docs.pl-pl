---
title: 'TN024: komunikaty i zasoby zdefiniowane przez MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 24bcacd46b839babe9c9c89facb1cc56d18c0ee5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370352"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024: komunikaty i zasoby zdefiniowane przez MFC

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

W tej notatce opisano wewnętrzne komunikaty systemu Windows i formaty zasobów używane przez MFC. Te informacje wyjaśniają implementację struktury i pomogą Ci w debugowaniu aplikacji. Dla przygód, mimo że wszystkie te informacje są oficjalnie nieobsługiwane, można użyć niektórych z tych informacji do zaawansowanych implementacji.

Ta uwaga zawiera szczegóły implementacji prywatnej MFC; wszystkie treści mogą ulec zmianie w przyszłości. Wiadomości mfc prywatnego systemu Windows mają znaczenie tylko w zakresie jednej aplikacji, ale zmieni się w przyszłości, aby zawierać wiadomości całego systemu.

Zakres wiadomości i typów zasobów mfc prywatnych systemu Windows znajdują się w zarezerwowanym zakresie "system" odłogowanym przez system Microsoft Windows. Obecnie nie wszystkie liczby w zakresach są używane, a w przyszłości mogą być używane nowe numery w zakresie. Aktualnie używane numery mogą ulec zmianie.

Wiadomości mfc prywatnego systemu Windows są w zakresie 0x360->0x37F.

Typy zasobów prywatnych MFC znajdują się w zakresie 0xF0->0xFF.

**Prywatne wiadomości systemu Windows MFC**

Te komunikaty systemu Windows są używane zamiast funkcji wirtualnych języka C++, gdzie stosunkowo luźne sprzężenie jest wymagane między obiektami okna i gdzie funkcja wirtualna języka C++ nie byłaby odpowiednia.

Te prywatne komunikaty systemu Windows i skojarzone struktury parametrów są deklarowane w prywatnym nagłówku MFC 'AFXPRIV. H'. Ostrzegamy, że dowolny kod, który zawiera ten nagłówek może polegać na nieudokumentowane zachowanie i prawdopodobnie przerwy w przyszłych wersjach MFC.

W rzadkich przypadkach konieczności obsługi jednego z tych komunikatów, należy użyć makra mapy ON_MESSAGE wiadomości i obsługi wiadomości w ogólnym formacie LRESULT/WPARAM/LPARAM.

**WM_QUERYAFXWNDPROC**

Ta wiadomość jest wysyłana do okna, które jest tworzone. Jest to wysyłane bardzo wcześnie w procesie tworzenia jako metoda określania, czy WndProc jest **AfxWndProc. AfxWndProc** zwraca wartość 1.

|||
|-|-|
|Wparam|Nieużywane|
|Lparam|Nieużywane|
|zwraca|1 w przypadku przetworzenia przez **AfxWndProc**|

**WM_SIZEPARENT**

Ten komunikat jest wysyłany przez okno ramki do`CFrameWnd::OnSize` `CFrameWnd::RecalcLayout` jego `CWnd::RepositionBars`bezpośrednich obrażeń podczas zmiany rozmiaru (wywołania, które wywołuje), aby zmienić położenie pasków sterowania wokół boku ramki. Struktura AFX_SIZEPARENTPARAMS zawiera bieżący prostokąt klienta dostępnego obiektu nadrzędnego i HDWP (który może `DeferWindowPos` być NULL), z którym można wywołać, aby zminimalizować ponowne malowanie.

|||
|-|-|
|Wparam|Nieużywane|
|Lparam|Adres struktury AFX_SIZEPARENTPARAMS|
|zwraca|Nieużyno (0)|

Ignorowanie komunikatu wskazuje, że okno nie bierze udziału w układzie.

**WM_SETMESSAGESTRING**

Ta wiadomość jest wysyłana do okna ramki z prośbą o zaktualizowanie wiersza wiadomości na pasku stanu. Można określić identyfikator ciągu lub LPCSTR (ale nie oba).

|||
|-|-|
|Wparam|Identyfikator ciągu (lub zero)|
|Lparam|LPCSTR dla ciągu (lub NULL)|
|zwraca|Nieużyno (0)|

**WM_IDLEUPDATECMDUI**

Ten komunikat jest wysyłany w czasie bezczynności, aby zaimplementować aktualizację interfejsu użytkownika w czasie bezczynności. Jeśli okno (zwykle pasek sterowania) obsługuje komunikat, `CCmdUI` tworzy obiekt (lub obiekt klasy pochodnej) i wywołać `CCmdUI::DoUpdate` dla każdego z "elementów" w oknie. To z kolei sprawdzić, czy ON_UPDATE_COMMAND_UI obsługi obiektów w łańcuchu obsługi poleceń.

|||
|-|-|
|Wparam|BOOL bDisableIfNoHandler|
|Lparam|Nieużyno (0)|
|zwraca|Nieużyno (0)|

*bDisableIfNoHandler* jest niezerowy, aby wyłączyć obiekt interfejsu użytkownika, jeśli nie ma ani ON_UPDATE_COMMAND_UI ani ON_COMMAND obsługi.

**WM_EXITHELPMODE**

Ten komunikat jest `CFrameWnd` publikowany w tym, aby zakończyć kontekstowy tryb pomocy. Odbiór tej wiadomości kończy pętlę modalną rozpoczętą przez `CFrameWnd::OnContextHelp`.

|||
|-|-|
|Wparam|Nieużyno (0)|
|Lparam|Nieużyno (0)|
|zwraca|Nieużywane|

**WM_INITIALUPDATE**

Ten komunikat jest wysyłany przez szablon dokumentu do wszystkich elementów podrzędnych okna ramki, gdy jest to bezpieczne dla nich, aby wykonać ich początkowej aktualizacji. Mapuje do wywołania, `CView::OnInitialUpdate` ale może `CWnd`być używany w innych klasy pochodne dla innych aktualizacji one-shot.

|||
|-|-|
|Wparam|Nieużyno (0)|
|Lparam|Nieużyno (0)|
|zwraca|Nieużyno (0)|

**WM_RECALCPARENT**

Ta wiadomość jest wysyłana przez widok do `GetParent`okna nadrzędnego (uzyskanego za pośrednictwem), aby `RecalcLayout`wymusić ponowne obliczenie układu (zwykle wywoła to element nadrzędny). Jest to używane w aplikacjach serwera OLE, gdzie jest to konieczne dla ramki do zwiększenia rozmiaru w miarę wzrostu całkowitego rozmiaru widoku.

Jeśli okno nadrzędne przetwarza ten komunikat, należy zwrócić wartość TRUE i wypełnić RECT przekazany w lParam nowym rozmiarem obszaru klienta. `CScrollView` Służy do prawidłowego obchodzenia się z paskami przewijania (umieść następnie na zewnątrz okna po dodaniu), gdy obiekt serwera jest aktywowany w miejscu.

|||
|-|-|
|Wparam|Nieużyno (0)|
|Lparam|LPRECT rectClient, może mieć wartość NULL|
|zwraca|PRAWDA, jeśli zwrócono nowy prostokąt klienta, FALSE w przeciwnym razie|

**WM_SIZECHILD**

Ten komunikat jest `COleResizeBar` wysyłany przez `GetOwner`do okna właściciela (przez), gdy użytkownik zmienia rozmiar paska zmiany rozmiaru z uchwytami zmiany rozmiaru. `COleIPFrameWnd`odpowiada na ten komunikat, próbując zmienić położenie okna ramki zgodnie z żądaniem użytkownika.

Nowy prostokąt, podany we współrzędnych klienta względem okna ramki, które zawiera pasek rozmiaru, jest wskazywalny przez lParam.

|||
|-|-|
|Wparam|Nieużyno (0)|
|Lparam|LPRECT rectNowy|
|zwraca|Nieużyno (0)|

**WM_DISABLEMODAL**

Ten komunikat jest wysyłany do wszystkich wyskakujących okienek należących do okna ramki, które jest dezaktywowane. Okno ramki używa wyniku, aby określić, czy wyłączyć okno podręczne.

Można użyć tego do wykonywania specjalnego przetwarzania w wyskakującym oknie, gdy ramka wejdzie w stan modalny lub aby niektóre okna podręczne nie zostały wyłączone. Etykietki narzędzi używają tego komunikatu, aby zniszczyć się, gdy okno ramki przechodzi do stanu modalnego, na przykład.

|||
|-|-|
|Wparam|Nieużyno (0)|
|Lparam|Nieużyno (0)|
|zwraca|Non-zero, aby **NIE** wyłączyć okna, 0 wskazuje, że okno zostanie wyłączone|

**WM_FLOATSTATUS**

Ten komunikat jest wysyłany do wszystkich wyskakujących okienek należących do okna ramki, gdy ramka jest aktywowana lub dezaktywowana przez inne okno ramki najwyższego poziomu. Jest to wykorzystywane przez implementację MFS_SYNCACTIVE `CMiniFrameWnd`w , aby utrzymać aktywację tych wyskakujących okienek zsynchronizowanych z aktywacją okna ramki najwyższego poziomu.

|||
|-|-|
|Wparam|Jest jedną z następujących wartości:<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|Lparam|Nieużyno (0)|

Zwracana wartość powinna być niezerowa, jeśli jest ustawiona FS_SYNCACTIVE, a okno synchronizuje jego aktywację z ramką nadrzędną. `CMiniFrameWnd`zwraca wartość niezerową, gdy styl jest ustawiony na MFS_SYNCACTIVE.

Aby uzyskać więcej informacji, `CMiniFrameWnd`zobacz implementację .

## <a name="wm_activatetoplevel"></a>WM_ACTIVATETOPLEVEL

Ten komunikat jest wysyłany do okna najwyższego poziomu, gdy okno w "grupie najwyższego poziomu" jest aktywowane lub dezaktywowane. Okno jest częścią grupy najwyższego poziomu, jeśli jest to okno najwyższego poziomu (bez nadrzędnego lub właściciela) lub jest własnością takiego okna. Ten komunikat jest podobny w użyciu do WM_ACTIVATEAPP, ale działa w sytuacjach, gdy okna należące do różnych procesów są mieszane w hierarchii jednego okna (typowe w aplikacjach OLE).

## <a name="wm_commandhelp-wm_helphittest-wm_exithelpmode"></a>WM_COMMANDHELP, WM_HELPHITTEST, WM_EXITHELPMODE

Te komunikaty są używane w implementacji pomocy kontekstowej. Więcej informacji można znaleźć w [notatce technicznej 28.](../mfc/tn028-context-sensitive-help-support.md)

## <a name="mfc-private-resource-formats"></a>Formaty zasobów prywatnych MFC

Obecnie MFC definiuje dwa formaty zasobów prywatnych: RT_TOOLBAR i RT_DLGINIT.

## <a name="rt_toolbar-resource-format"></a>RT_TOOLBAR format zasobu

Domyślny pasek narzędzi dostarczony przez AppWizard jest oparty na RT_TOOLBAR zasobu niestandardowego, który został wprowadzony w MFC 4.0. Zasób ten można edytować za pomocą edytora paska narzędzi.

## <a name="rt_dlginit-resource-format"></a>RT_DLGINIT format zasobu

Jeden format zasobów prywatnych MFC jest używany do przechowywania dodatkowych informacji inicjowania okna dialogowego. Obejmuje to początkowe ciągi przechowywane w polu kombi. Format tego zasobu nie jest przeznaczony do edycji ręcznej, ale jest obsługiwany przez visual C++.

Visual C++ i ten RT_DLGINIT zasób nie są wymagane do korzystania z powiązanych funkcji MFC, ponieważ istnieją alternatywy interfejsu API przy użyciu informacji w zasobie. Za pomocą języka Visual C++ znacznie ułatwia pisanie, obsługa i tłumaczenie aplikacji w dłuższej perspektywie.

Podstawowa struktura zasobu RT_DLGINIT jest następująca:

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

Powtórzona sekcja zawiera identyfikator formantu, do który ma wysłać wiadomość, wiadomość # do wysłania (normalna wiadomość systemu Windows) i zmienną długość danych. Wiadomość systemu Windows jest wysyłana w formularzu:

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

Jest to bardzo ogólny format, umożliwiający wszelkie wiadomości systemu Windows i zawartość danych. Edytor zasobów języka Visual C++ i MFC obsługują tylko ograniczony podzbiór komunikatów systemu Windows: CB_ADDSTRING dla początkowych opcji listy dla pól kombi (dane są ciągiem tekstowym).

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
