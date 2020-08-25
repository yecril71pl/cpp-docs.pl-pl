---
title: 'TN024: komunikaty i zasoby zdefiniowane przez MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 9ad6827e4a46bb9f2ff3b02986a01737772e0858
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839221"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024: komunikaty i zasoby zdefiniowane przez MFC

> [!NOTE]
> Następująca Uwaga techniczna nie została zaktualizowana, ponieważ została najpierw uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zalecamy wyszukiwanie tematu zainteresowania w indeksie dokumentacji online.

Ta Uwaga zawiera opis wewnętrznych komunikatów systemu Windows i formatów zasobów używanych przez MFC. Te informacje wyjaśniają implementację struktury i ułatwiają debugowanie aplikacji. W przypadku Adventurous, mimo że wszystkie te informacje są oficjalnie nieobsługiwane, możesz użyć niektórych z tych informacji dla zaawansowanych implementacji.

Ta Uwaga zawiera szczegóły dotyczące prywatnej implementacji MFC; Cała zawartość może ulec zmianie w przyszłości. Prywatne komunikaty systemu Windows MFC mają znaczenie tylko w zakresie jednej aplikacji, ale zmienią się w przyszłości, aby zawierały komunikaty systemowe.

Zakres prywatnych komunikatów systemu Windows i typów zasobów w bibliotece MFC znajduje się w zarezerwowanym zakresie "system", który jest ustawiony w systemie Microsoft Windows. Obecnie nie wszystkie liczby w zakresach są używane i w przyszłości mogą być używane nowe numery z zakresu. Obecnie używane numery mogą zostać zmienione.

Prywatne komunikaty systemu Windows MFC są w zakresie 0x360->0x37F.

Typy zasobów prywatnych MFC znajdują się w zakresie 0xF0->0xFF.

**Prywatne komunikaty systemu Windows MFC**

Te komunikaty systemu Windows są używane zamiast funkcji wirtualnych języka C++, gdzie względnie swobodne sprzężenie jest wymagane między obiektami okna a funkcją wirtualną języka C++ nie jest odpowiednia.

Te prywatne komunikaty systemu Windows i skojarzone struktury parametrów są zadeklarowane w prywatnym nagłówku MFC "AFXPRIV". H '. Należy ostrzec, że dowolny kod, który zawiera ten nagłówek, może polegać na nieudokumentowanym zachowaniu i prawdopodobnie ulegnie przerwaniu w przyszłych wersjach MFC.

W rzadkim przypadku potrzeby obsługi jednego z tych komunikatów należy użyć makra mapy komunikatów ON_MESSAGE i obsłużyć komunikat w formacie generycznego LRESULT/WPARAM/LPARAM.

**WM_QUERYAFXWNDPROC**

Ta wiadomość jest wysyłana do tworzonego okna. Jest to wysyłane bardzo wcześnie w procesie tworzenia jako metoda określania, czy WndProc jest **AfxWndProc. AfxWndProc** zwraca 1.

| Parametry i wartość zwracana | Opis |
|-|-|
|wParam|Nieużywane|
|lParam|Nieużywane|
|zwraca|1 w przypadku przetworzenia przez **AfxWndProc**|

**WM_SIZEPARENT**

Ten komunikat jest wysyłany przez okno ramki do jego bezpośrednich elementów podrzędnych podczas zmiany rozmiarów ( `CFrameWnd::OnSize` wywołuje `CFrameWnd::RecalcLayout` , które wywołania `CWnd::RepositionBars` ), aby zmienić położenie pasków sterowania wokół krawędzi ramki. Struktura AFX_SIZEPARENTPARAMS zawiera bieżący dostępny prostokąt klienta elementu nadrzędnego i HDWP (który może mieć wartość NULL), z którym należy wywołać, `DeferWindowPos` Aby zminimalizować odświeżenie.

| Parametry i wartość zwracana | Opis |
|-|-|
|wParam|Nieużywane|
|lParam|Adres struktury AFX_SIZEPARENTPARAMS|
|zwraca|Nieużywane (0)|

Komunikat informujący o tym, że okno nie jest częścią układu.

**WM_SETMESSAGESTRING**

Ten komunikat jest wysyłany do okna ramki, aby poprosił go o aktualizację wiersza komunikatu na pasku stanu. Można określić identyfikator ciągu lub LPCSTR (ale nie oba).

| Parametry i wartość zwracana | Opis |
|-|-|
|wParam|Identyfikator ciągu (lub zero)|
|lParam|LPCSTR dla ciągu (lub wartości NULL)|
|zwraca|Nieużywane (0)|

**WM_IDLEUPDATECMDUI**

Ta wiadomość jest wysyłana w czasie bezczynności w celu zaimplementowania aktualizacji czasu bezczynności programów obsługi interfejsu wiersza polecenia aktualizacji. Jeśli okno (zazwyczaj pasek sterowania) obsługuje komunikat, tworzy `CCmdUI` obiekt (lub obiekt klasy pochodnej) i wywołuje `CCmdUI::DoUpdate` dla każdego elementu "Items" w oknie. Spowoduje to wyszukanie programu obsługi ON_UPDATE_COMMAND_UI dla obiektów w łańcuchu obsługi poleceń.

| Parametry i wartość zwracana | Opis |
|-|-|
|wParam|BDisableIfNoHandler BOOL|
|lParam|Nieużywane (0)|
|zwraca|Nieużywane (0)|

*bDisableIfNoHandler* jest różna od zera, aby wyłączyć obiekt interfejsu użytkownika, jeśli nie ma ON_UPDATE_COMMAND_UI ani ON_COMMAND obsługi.

**WM_EXITHELPMODE**

Ta wiadomość jest wysyłana do programu w `CFrameWnd` celu zakończenia trybu pomocy kontekstowej. Otrzymanie tej wiadomości kończy pętlę modalną uruchomioną przez `CFrameWnd::OnContextHelp` .

| Parametr i wartość zwracana | Opis |
|-|-|
|wParam|Nieużywane (0)|
|lParam|Nieużywane (0)|
|zwraca|Nieużywane|

**WM_INITIALUPDATE**

Ten komunikat jest wysyłany przez szablon dokumentu do wszystkich elementów podrzędnych okna ramki, gdy jest bezpieczny dla nich, aby wykonać ich początkową aktualizację. Mapuje do wywołania, `CView::OnInitialUpdate` ale mogą być używane w innych `CWnd` klasach pochodnych do innej aktualizacji z jednym zdjęciem.

| Parametry i wartość zwracana | Opis |
|-|-|
|wParam|Nieużywane (0)|
|lParam|Nieużywane (0)|
|zwraca|Nieużywane (0)|

**WM_RECALCPARENT**

Ten komunikat jest wysyłany przez widok do okna nadrzędnego (uzyskany przez `GetParent` program) w celu wymuszenia ponownego obliczenia układu (zazwyczaj jest to wywołanie nadrzędne `RecalcLayout` ). Ta wartość jest używana w aplikacjach serwera OLE, gdy jest to konieczne, aby rozmiar ramki został powiększony w miarę wzrostu całkowitego rozmiaru widoku.

Jeśli okno nadrzędne przetwarza ten komunikat, powinien zwrócić wartość TRUE i wypełnić obiekt RECT przekazaną w lParam z nowym rozmiarem obszaru klienckiego. Jest on używany w programie `CScrollView` , aby prawidłowo obsługiwać paski przewijania (umieść je na zewnątrz okna podczas dodawania), gdy obiekt serwera jest aktywowany w miejscu.

| Parametry i wartość zwracana | Opis |
|-|-|
|wParam|Nieużywane (0)|
|lParam|LPRECT rectClient może mieć wartość NULL|
|zwraca|Wartość TRUE, Jeśli zwracany jest nowy prostokąt klienta; w przeciwnym razie wartość FALSE|

**WM_SIZECHILD**

Ten komunikat jest wysyłany przez program `COleResizeBar` do okna właściciela (przez `GetOwner` ), gdy użytkownik zmienia rozmiar paska zmiany rozmiaru o uchwyty zmiany rozmiaru. `COleIPFrameWnd` reaguje na ten komunikat, próbując zmienić położenie okna ramki jako zażądanego przez użytkownika.

Nowy prostokąt, określony we współrzędnych klienta względem okna ramki zawierającego pasek zmiany rozmiaru, jest wskazywany przez lParam.

| Parametry i wartość zwracana | Opis |
|-|-|
|wParam|Nieużywane (0)|
|lParam|LPRECT rectNew|
|zwraca|Nieużywane (0)|

**WM_DISABLEMODAL**

Ta wiadomość jest wysyłana do wszystkich podręcznych okien należących do okna ramki, które jest dezaktywowane. Okno ramki używa wyniku, aby określić, czy wyłączyć okno podręczne.

Możesz użyć tego do przeprowadzenia specjalnego przetwarzania w oknie podręcznym, gdy ramka przejdzie do stanu modalnego lub aby wyłączyć niektóre okna podręczne. Etykietki narzędzi używają tego komunikatu, aby zniszczyć siebie, gdy okno ramki przechodzi do stanu modalnego, na przykład.

| Parametry i wartość zwracana | Opis |
|-|-|
|wParam|Nieużywane (0)|
|lParam|Nieużywane (0)|
|zwraca|Nie zero, aby **nie** wyłączać okna, 0 wskazuje, że okno zostanie wyłączone|

**WM_FLOATSTATUS**

Ten komunikat jest wysyłany do wszystkich okien podręcznych należących do okna ramki, gdy ramka zostanie aktywowana lub zdezaktywowana przez inne okno ramki najwyższego poziomu. Jest on używany przez implementację MFS_SYNCACTIVE w `CMiniFrameWnd` , aby zachować aktywację tych okien podręcznych w synchronizacji z aktywacją okna ramki najwyższego poziomu.

| Parametry | Opis |
|-|-|
|wParam|Jest jedną z następujących wartości:<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|Nieużywane (0)|

Wartość zwracana powinna być różna od zera, jeśli FS_SYNCACTIVE jest ustawiona, a okno syncronizes jego aktywację z ramką nadrzędną. `CMiniFrameWnd` Zwraca wartość różną od zera, gdy styl jest ustawiony na MFS_SYNCACTIVE.

Aby uzyskać więcej informacji, zobacz implementację programu `CMiniFrameWnd` .

## <a name="wm_activatetoplevel"></a>WM_ACTIVATETOPLEVEL

Ten komunikat jest wysyłany do okna najwyższego poziomu, gdy okno w jego grupie najwyższego poziomu jest aktywowane lub dezaktywowane. Okno jest częścią grupy najwyższego poziomu, jeśli jest oknem najwyższego poziomu (brak rodzica lub właściciela) lub należy do tego okna. Ten komunikat jest podobny do WM_ACTIVATEAPP, ale działa w sytuacjach, gdy system Windows należący do różnych procesów jest mieszany w jednej hierarchii okna (najczęściej w aplikacjach OLE).

## <a name="wm_commandhelp-wm_helphittest-wm_exithelpmode"></a>WM_COMMANDHELP, WM_HELPHITTEST, WM_EXITHELPMODE

Te komunikaty są używane w implementacji pomocy kontekstowej. Aby uzyskać więcej informacji, zapoznaj się z [uwagą techniczną 28](../mfc/tn028-context-sensitive-help-support.md) .

## <a name="mfc-private-resource-formats"></a>Formaty zasobów prywatnych MFC

Obecnie MFC definiuje dwa formaty zasobów prywatnych: RT_TOOLBAR i RT_DLGINIT.

## <a name="rt_toolbar-resource-format"></a>RT_TOOLBAR format zasobu

Domyślny pasek narzędzi dostarczany przez AppWizard jest oparty na RT_TOOLBAR niestandardowego zasobu, który został wprowadzony w MFC 4,0. Można edytować ten zasób przy użyciu edytora pasków narzędzi.

## <a name="rt_dlginit-resource-format"></a>RT_DLGINIT format zasobu

Jeden format prywatnego zasobu MFC służy do przechowywania dodatkowych informacji o inicjalizacji okna dialogowego. Obejmuje to początkowe ciągi przechowywane w polu kombi. Format tego zasobu nie jest zaprojektowany do ręcznego edytowania, ale jest obsługiwany przez Visual C++.

Visual C++ i ten zasób RT_DLGINIT nie jest wymagany do korzystania z pokrewnych funkcji MFC, ponieważ istnieje alternatywa interfejsu API do użycia informacji w zasobie. Używanie Visual C++ ułatwia pisanie, konserwowanie i translację aplikacji w długim przebiegu.

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

Powtórzona sekcja zawiera identyfikator kontrolki, do której zostanie wysłany komunikat, wiadomość # do wysłania (normalny komunikat systemu Windows) i zmienną długość danych. Wiadomość systemu Windows jest wysyłana w postaci:

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

Jest to ogólny format, który umożliwia dowolnych komunikatów systemu Windows i zawartości danych. Edytor zasobów Visual C++ i MFC obsługują tylko ograniczony podzestaw komunikatów systemu Windows: CB_ADDSTRING dla początkowych opcji listy dla pól kombi (dane są ciągami tekstowymi).

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numeru](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
