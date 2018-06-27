---
title: 'TN024: Komunikaty zdefiniowane przez MFC i zasoby | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a21ae615a3f4c644f6f0aa7c8f1306378a00ae5c
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36957188"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024: komunikaty i zasoby zdefiniowane przez MFC
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga opisuje wewnętrzne komunikaty systemu Windows i formatów zasobów używanych przez MFC. Tych informacji opisano implementacji platformy, a może pomóc w debugowaniu aplikacji. Dla adventurous nawet jeśli te informacje jest oficjalnie obsługiwana, można użyć niektóre z tych informacji w przypadku zaawansowanych implementacji.  
  
 Ta uwaga zawiera szczegóły prywatna implementacja MFC; Cała zawartość mogą ulec zmianie w przyszłości. MFC prywatnej komunikaty systemu Windows mają znaczenie w zakresie tylko jedną aplikację, ale zmieni się w przyszłości zawierać komunikaty systemowe.  
  
 Zakres MFC prywatnej komunikaty systemu Windows i typy zasobów są w zakresie zastrzeżonych "system" wydzielone Microsoft Windows. Obecnie nie wszystkie liczby w zakresach są używane, i w przyszłości, można użyć nowych numerów w zakresie. Aktualnie używanych numerów mogą ulec zmianie.  
  
 MFC Windows prywatnej wiadomości znajdują się w zakresie 0x360 -> 0x37F.  
  
 MFC zasobem prywatnej typów znajdują się w zakresie 0xF0 -> 0xFF.  
  
 **Komunikaty systemu Windows prywatnego MFC**  
  
 Te komunikaty systemu Windows są używane zamiast funkcji wirtualnych C++, w których jest wymagane stosunkowo luźne powiązanie między obiektami okien i gdzie C++ funkcji wirtualnej nie jest właściwe.  
  
 Tych prywatnych komunikaty systemu Windows i skojarzony parametr struktury są zadeklarowane w nagłówku prywatnej MFC "AFXPRIV. H ". Otrzymywać ostrzeżenie, że wszelkie swój kod, który zawiera ten nagłówek może zależało od nieudokumentowanej zachowanie i podział prawdopodobnie będzie w przyszłości wersji biblioteki MFC.  
  
 W przypadku rzadkich konieczności obsługi jednego z tych wiadomości należy użyć on_message — makro mapy wiadomości i obsługi wiadomości w formacie ogólnego elementu LRESULT/WPARAM/LPARAM.  
  
 **WM_QUERYAFXWNDPROC**  
  
 Ten komunikat jest wysyłane do okna, która jest tworzona. To są wysyłane bardzo wcześnie w procesie tworzenia jako metoda określenie, czy WndProc **AfxWndProc. AfxWndProc** zwraca wartość 1.  
  
|||  
|-|-|  
|wParam|Nieużywane|  
|lParam|Nieużywane|  
|zwraca|1, jeśli przetworzone przez **AfxWndProc**|  
  
 **WM_SIZEPARENT**  
  
 Ten komunikat jest wysyłany przez okno ramowe do jego bezpośrednie elementy podrzędne podczas zmiany rozmiaru (`CFrameWnd::OnSize` wywołania `CFrameWnd::RecalcLayout` które wywołuje `CWnd::RepositionBars`) Aby zmienić położenie paski sterowania wokół części ramki. Struktura AFX_SIZEPARENTPARAMS zawiera bieżący prostokąt dostępne klienta nadrzędnego i HDWP, (co może mieć wartości NULL) umożliwiające wywołać `DeferWindowPos` aby zminimalizować ponownego rysowania.  
  
|||  
|-|-|  
|wParam|Nieużywane|  
|lParam|Adres AFX_SIZEPARENTPARAMS — struktura|  
|zwraca|Nieużywane (0)|  
  
 Zignorowanie komunikatu wskazuje, że okno nie uczestniczy w układzie.  
  
 **WM_SETMESSAGESTRING**  
  
 Ten komunikat jest wysyłane do okno ramowe zapytać, aby zaktualizować wiersz wiadomości w pasku stanu. Identyfikator ciągu lub LPCSTR może być określony (ale nie oba).  
  
|||  
|-|-|  
|wParam|Ciąg Identyfikatora (lub zero)|  
|lParam|LPCSTR ciąg (lub wartość NULL)|  
|zwraca|Nieużywane (0)|  
  
 **WM_IDLEUPDATECMDUI**  
  
 Czas bezczynności wysyłane tej wiadomości do zaimplementowania aktualizacja czas bezczynności polecenia update obsługi interfejsu użytkownika. Jeśli okno (zazwyczaj pasek sterowania) obsługuje wiadomości, tworzy `CCmdUI` (lub obiektu klasy pochodnej) i Wywołaj `CCmdUI::DoUpdate` dla poszczególnych elementów"" w oknie. Z kolei spowoduje to zaewidencjonowanie obsługi on_update_command_ui — dla obiektów w łańcuchu programu obsługi poleceń.  
  
|||  
|-|-|  
|wParam|Wartość logiczna bDisableIfNoHandler|  
|lParam|Nieużywane (0)|  
|zwraca|Nieużywane (0)|  
  
 *bDisableIfNoHandler* jest różna od zera, aby wyłączyć obiekt interfejsu użytkownika w przypadku obsługi on_command — ani on_update_command_ui —.  
  
 **WM_EXITHELPMODE**  
  
 Ten komunikat jest zamieszczana `CFrameWnd` aby zakończyć kontekstowej pomocy technicznej trybu. Odebranie tej wiadomości kończy tryb pętli modalnej uruchomione przez `CFrameWnd::OnContextHelp`.  
  
|||  
|-|-|  
|wParam|Nieużywane (0)|  
|lParam|Nieużywane (0)|  
|zwraca|Nieużywane|  
  
 **WM_INITIALUPDATE**  
  
 Ten komunikat jest wysyłany przez szablonu dokumentu do wszystkich elementów podrzędnych okno ramowe, gdy jest bezpieczne, należy ich aktualizacji początkowej. Mapuje wywołanie `CView::OnInitialUpdate` , ale można używać w innych `CWnd`-klas innych aktualizacji jednorazowej pochodnych.  
  
|||  
|-|-|  
|wParam|Nieużywane (0)|  
|lParam|Nieużywane (0)|  
|zwraca|Nieużywane (0)|  
  
 **WM_RECALCPARENT**  
  
 Ten komunikat jest wysyłany przez widok do jej okna nadrzędnego (uzyskanych za pośrednictwem `GetParent`) aby wymusić ponowne obliczanie układu (zazwyczaj wywoła element nadrzędny `RecalcLayout`). Służy to w aplikacje serwera OLE gdzie jest to konieczne dla ramki zwiększa się rozmiar wraz z rozwojem całkowity rozmiar widoku.  
  
 Jeśli okno nadrzędne przetwarza ten komunikat powinien zwrócić wartość TRUE i wypełnienia RECT przekazano lParam z nowy rozmiar obszaru klienckiego. Jest on używany w `CScrollView` poprawnie obsługiwać pasków przewijania (miejsce na zewnątrz okna, jeśli są one dodawane) gdy obiekt serwera jest aktywowana w miejscu.  
  
|||  
|-|-|  
|wParam|Nieużywane (0)|  
|lParam|RectClient lprect — może mieć wartości NULL|  
|zwraca|Wartość TRUE, jeśli jest to nowy klient prostokąt zwróciła, wartość FALSE w przeciwnym razie|  
  
 **WM_SIZECHILD**  
  
 Ten komunikat jest wysyłany przez `COleResizeBar` do jej okna nadrzędnego (za pośrednictwem `GetOwner`) gdy użytkownik zmienia rozmiar pasek z uchwytami zmiany rozmiaru. `COleIPFrameWnd` reaguje na tę wiadomość próby zmiany położenia okno ramowe, ponieważ użytkownik zgłosił żądanie.  
  
 Nowy prostokąt, podany w współrzędne klienta względem ramkę okna zawierającą pasek, jest wskazywanego przez lParam.  
  
|||  
|-|-|  
|wParam|Nieużywane (0)|  
|lParam|Lprect — rectNew|  
|zwraca|Nieużywane (0)|  
  
 **WM_DISABLEMODAL**  
  
 Ten komunikat jest wysyłane do wszystkich okien wyskakujących własnością okno ramowe, która jest dezaktywowana. Okno ramowe używa wynik do ustalenia, czy wyłączyć w oknie podręcznym.  
  
 Można to wykonać specjalnego przetwarzania w wyskakującym oknie, gdy ramka przechodzi do stanu modalnego lub zapobiec niektórych wyskakujące pobierania wyłączone. Etykietki narzędzi umożliwia zniszczyć się, gdy okno ramowe przechodzi w stan modalny, na przykład tego komunikatu.  
  
|||  
|-|-|  
|wParam|Nieużywane (0)|  
|lParam|Nieużywane (0)|  
|zwraca|Niezerowa do **nie** wyłączaj okno, 0 wskazuje okno zostanie wyłączone|  
  
 **WM_FLOATSTATUS**  
  
 Ten komunikat jest wysyłany do wszystkich okien wyskakujących, własnością okno ramowe, gdy ramki jest aktywowane lub dezaktywowane przez inne okno ramowego najwyższego poziomu. To jest używany przez implementację MFS_SYNCACTIVE w `CMiniFrameWnd`, aby synchronizować Aktywacja tych okien wyskakujących w aktywacji najwyższego poziomu ramkę okna.  
  
|||  
|-|-|  
|wParam|Jest jednym z następujących wartości:<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|  
|lParam|Nieużywane (0)|  
  
 Wartość zwracana powinna być niezerowy Jeśli FS_SYNCACTIVE jest zestaw i synchronizuje okna aktywacji z ramka nadrzędny. `CMiniFrameWnd` Zwraca inną niż zero, jeżeli styl jest równy MFS_SYNCACTIVE.  
  
 Aby uzyskać więcej informacji, zobacz wykonania `CMiniFrameWnd`.  
  
## <a name="wmactivatetoplevel"></a>WM_ACTIVATETOPLEVEL  
 Ten komunikat jest wysyłany do okna najwyższego poziomu, gdy okno w jego "grupa najwyższego poziomu" jest aktywowane lub dezaktywowane. Okno jest częścią grupy najwyższego poziomu, jeśli okno najwyższego poziomu (nie nadrzędnej lub właściciela), lub jego właścicielem jest okno programu. Ten komunikat jest podobnie jak WM_ACTIVATEAPP, ale działa w sytuacjach, w których są należących do różnych procesów systemu windows zawiera mieszane (często używane w aplikacji OLE) hierarchii jednego okna.  
  
## <a name="wmcommandhelp-wmhelphittest-wmexithelpmode"></a>WM_EXITHELPMODE WM_COMMANDHELP, WM_HELPHITTEST,  
 Komunikaty te są używane w implementacji pomoc kontekstową. Zapoznaj się z [28 Uwaga techniczna](../mfc/tn028-context-sensitive-help-support.md) Aby uzyskać więcej informacji.  
  
## <a name="mfc-private-resource-formats"></a>Formatów zasobów prywatnego MFC  
 Obecnie MFC definiuje dwie prywatne zasobów w formatach: rt_toolbar — i RT_DLGINIT.  
  
## <a name="rttoolbar-resource-format"></a>Rt_toolbar — zasób formatu  
 Narzędzi domyślne, dostarczone przez kreatorami AppWizard jest oparta na rt_toolbar — zasób niestandardowy, który został wprowadzony w MFC 4.0. Można edytować tego zasobu, używając Edytor paska narzędzi.  
  
## <a name="rtdlginit-resource-format"></a>Format zasobu RT_DLGINIT  
 Jeden format prywatnej zasobu MFC służy do przechowywania informacji na temat inicjalizacji dodatkowe okna dialogowego. W tym początkowej ciągi przechowywane w polu kombi. Format ten zasób nie jest przeznaczony do można ręcznie edytować, ale jest obsługiwany przez Visual C++.  
  
 Visual C++ i ten zasób RT_DLGINIT nie trzeba użyć pokrewne funkcje MFC, ponieważ istnieją zamiast interfejsu API, korzystając z informacji w zasobie. Za pomocą języka Visual C++ ułatwia do zapisu, obsługa i tłumaczenie w dłuższej perspektywie aplikacji.  
  
 Podstawowa struktura zasobu RT_DLGINIT znajduje się w następujący sposób:  
  
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
  
 Powtórzony sekcja zawiera identyfikator formantu, który można wysłać komunikatu, komunikat # Wyślij (normalne komunikatów systemu Windows) i danych o zmiennej długości. Komunikatów systemu Windows są wysyłane w postaci:  
  
```  
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```  
  
 Jest to bardzo ogólne format, dzięki czemu wszystkie komunikaty systemu Windows i zawartości danych. Edytor zasobów programu Visual C++ i MFC obsługują tylko ograniczonym podzbiorem komunikaty systemu Windows: CB_ADDSTRING dla początkowych opcji listy dla pola kombi (danych to ciąg tekstowy).  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

