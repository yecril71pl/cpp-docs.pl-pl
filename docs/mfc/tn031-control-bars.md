---
title: 'TN031: Paski sterowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls.bars
dev_langs:
- C++
helpviewer_keywords:
- control bars [MFC], styles
- CStatusBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], deriving from
- control bars [MFC], classes [MFC]
- CDialogBar class [MFC], Tech Note 31 usage
- CToolBar class [MFC], Tech Note 31 usage
- TN031
- styles [MFC], control bars
ms.assetid: 8cb895c0-40ea-40ef-90ee-1dd29f34cfd1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1d5cc113177a9653e709c14f66682959276e7ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tn031-control-bars"></a>TN031: paski sterowania
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Klasy pasków sterowania w MFC opisuje ta Uwaga: Ogólne [ccontrolbar —](#_mfcnotes_ccontrolbar), [cstatusbar —](#_mfcnotes_cstatusbar), [ctoolbar —](#_mfcnotes_ctoolbar), [cdialogbar —](#_mfcnotes_cdialogbar)i  **CDockBar**.  
  
## <a name="_mfcnotes_ccontrolbar"></a> Ccontrolbar — 
  
 A **ControlBar** jest `CWnd`-pochodnej klasy, które:  
  
-   Jest wyrównany do góry lub u dołu okna ramki.  
  
-   Może zawierać elementy podrzędne, które są albo formantów na podstawie HWND (na przykład `CDialogBar`) lub z systemem innym niż-`HWND` na podstawie elementów (na przykład `CToolBar`, `CStatusBar`).  
  
 Paski sterowania obsługuje dodatkowe style:  
  
- `CBRS_TOP` (Opcja domyślna) Przypnij pasek sterowania do góry.  
  
- `CBRS_BOTTOM` Przypnij pasek sterowania na dole.  
  
- `CBRS_NOALIGN` Nie zmienia położenie pasek sterowania, gdy zmienia rozmiar obiektu nadrzędnego.  
  
 Klasy wyprowadzone z `CControlBar` zapewniają bardziej interesującego implementacji:  
  
- `CStatusBar` Pasek stanu elementy są zawierającej tekst okienka paska stanu.  
  
- `CToolBar` Pasek narzędzi elementy są wyrównane w wierszu przycisków mapy bitowej.  
  
- `CDialogBar` Ramka pasek narzędzi zawierające standardowego systemu windows formantów (utworzone na podstawie zasobu szablonu okna dialogowego).  
  
- **CDockBar** uogólniony miejsce dokowania dla innych `CControlBar` pochodnych obiektów. Określonego elementu członkowskiego, funkcje i zmienne, dostępne w tej klasie mogą ulec zmianie w przyszłych wersjach.  
  
 Wszystkie kontrolki paska obiektów/system windows będzie okien podrzędnych okien ramka nadrzędny. Są one zazwyczaj dodane jako element równorzędny do obszaru klienckiego ramki (na przykład klienta MDI lub Widok). Ważne jest identyfikator okna podrzędnego pasek sterowania. Domyślny układ pasek sterowania działa tylko dla paski sterowania z identyfikatorami w zakresie **AFX_IDW_CONTROLBAR_FIRST** do **AFX_IDW_CONTROLBAR_LAST**. Należy pamiętać, że nawet jeśli istnieje szereg kontroli 256 paska identyfikatory, pierwszy 32 te pasek sterowania identyfikatory są specjalne ponieważ są bezpośrednio obsługiwane przez architektura podglądu wydruku.  
  
 `CControlBar` Klasy daje standardowej implementacji dla:  
  
-   Wyrównywanie pasek sterowania u góry, dołu lub obu stronach ramki.  
  
-   Przydzielanie kontroli tablice elementów.  
  
-   Obsługa implementacja klas pochodnych.  
  
 Obiekty pasków sterowania C++ zazwyczaj zostanie osadzony jako elementy członkowskie `CFrameWnd` klasy i zostaną wyczyszczone kiedy nadrzędnego `HWND` i obiektu zostaną zniszczone. Można przydzielić obiektu pasek sterowania na stercie należy po prostu można ustawić **m_bAutoDestruct** członka **TRUE** aby pasek sterowania "**usunąć ten**" podczas `HWND` zostanie zniszczony.  
  
> [!NOTE]
>  W przypadku utworzenia własnych `CControlBar`-pochodnej klasy, a nie przy użyciu jednej z jego MFC klasy pochodne —, takich jak `CStatusBar`, `CToolBar`, lub `CDialogBar`, musisz ustawić `m_dwStyle` element członkowski danych. Można to zrobić w zastąpieniu z **Utwórz**:  
  
```  
// CMyControlBar is derived from CControlBar  
BOOL CMyControlBar::Create(CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID)  
{  
    m_dwStyle = dwStyle;  
 
 .  
 .  
 .  
}  
```  
  
 **Algorytm układu pasek sterowania**  
  
 Algorytm układu pasek sterowania jest bardzo prosty. Okno ramowe wysyła komunikat **WM_SIZEPARENT** do wszystkich obiektów podrzędnych w zakresie pasek sterowania. Wraz z tego komunikatu jest przekazywany wskaźnik do elementu nadrzędnego klienta prostokąta. Ten komunikat jest wysyłane do elementów podrzędnych w porządku osi Z. Te informacje służą podrzędnych pasków sterowania, aby pozycjonują się i zmniejszyć rozmiar obszaru klienckiego elementu nadrzędnego. Prostokąt końcowego pozostało dla obszaru klienckiego normalne (mniej paski sterowania) służy do położenie okna głównego klienta (zazwyczaj klienta, widoku lub podziału okna MDI).  
  
 Zobacz `CWnd::RepositionBars` i `CFrameWnd::RecalcLayout` więcej szczegółów.  
  
 MFC prywatnej komunikatów systemu Windows, w tym **WM_SIZEPARENT**, są udokumentowane w artykule [24 Uwaga techniczna](../mfc/tn024-mfc-defined-messages-and-resources.md).  
  
## <a name="_mfcnotes_cstatusbar"></a>  Cstatusbar —  
  
 Pasek stanu jest pasek sterowania, który zawiera wiersz okienek tekstu wyjściowego. Istnieją dwa podstawowe sposoby użycia okienek tekstu wyjściowego:  
  
-   Jako wiersz wiadomości  
  
     (na przykład standardowe menu Pomoc wiersza komunikatu). Te zwykle są używane przez 0 systemem indeksowane  
  
-   Jako wskaźniki stanu  
  
     (na przykład centralnych zasad dostępu, NUM SCRL wskaźniki i). Te zwykle są używane przez identyfikator ciągu/polecenia.  
  
 Czcionka na pasku stanu jest punkt 10 MS Sans Serif (ustawieniem Podręcznik projektowania aplikacji interfejsu systemu Windows lub czcionki mapowań najlepsze dopasowanie 10 punktów Szwajcarii czcionki proporcjonalne). W niektórych wersjach systemu Windows, takich jak wersja japońska czcionki wybrane są różne.  
  
 Kolory używane w pasku stanu również są spójne z zaleceniem Podręcznik projektowania aplikacji interfejsu systemu Windows. Kolory twarde nie są zakodowane i są zmieniane dynamicznie w odpowiedzi na dostosowaniem wprowadzanym przez użytkowników w Panelu sterowania.  
  
|Element|Wartości kolorów systemu Windows|Domyślne RGB|  
|----------|-------------------------|-----------------|  
|Tło paska stanu|**COLOR_BTNFACE**|RGB (192, 192, 192)|  
|Tekst paska stanu|**COLOR_BTNTEXT**|RGB (000 000, 000)|  
|Krawędziach górnego/lewego — pasek stanu|**COLOR_BTNHIGHLIGHT**|RGB (255 255, 255)|  
|Stan paska bot/prawej krawędzi.|**COLOR_BTNSHADOW**|RGB (128, 128, 128)|  
  
 **Cstatusbar — ccmdui — Obsługa**  
  
 Jest sposób wskaźniki zwykle są aktualizowane za pośrednictwem `ON_UPDATE_COMMAND_UI` mechanizmu. Na czas bezczynności, wywoła pasek stanu `ON_UPDATE_COMMAND_UI` obsługi o identyfikatorze ciąg w okienku wskaźnika.  
  
 `ON_UPDATE_COMMAND_UI` Obsługi można wywołać:  
  
- **Włącz**: Aby włączyć lub wyłączyć okienka. Okienko wyłączone wygląda tak samo jak okienko włączone, ale tekst jest niewidoczne (to znaczy wyłącza wskaźnik).  
  
- **SetText**: Aby zmienić tekst. Należy zachować ostrożność, jeśli używasz to ponieważ okienku nie automatycznego zmieniania rozmiaru.  
  
 Odwołuje się do klasy [cstatusbar —](../mfc/reference/cstatusbar-class.md) w *informacje dotyczące biblioteki klas* szczegółowe informacje o `CStatusBar` tworzenia i dostosowywania interfejsów API. Większość Dostosowywanie pasków stanu należy zrobić przed na pasku stanu jest początkowo stają się widoczne.  
  
 Pasek stanu obsługuje tylko jedno okienko stretchy zwykle pierwszego okienka. Rozmiar okienka naprawdę jest minimalny rozmiar. Jeśli na pasku stanu jest większy niż minimalny rozmiar wszystkich okienek, wszelkie dodatkowe szerokość otrzyma stretchy okienka. Domyślną aplikację z paskiem stanu ma wyrównany wskaźniki centralnych zasad dostępu, NUM i SCRL, ponieważ pierwszy okienko jest stretchy.  
  
## <a name="_mfcnotes_ctoolbar"></a>  Ctoolbar —  
  
 Pasek narzędzi jest pasek sterowania z rzędu przycisków mapy bitowej, które mogą zawierać separatorów. Obsługiwane są dwa style przyciski: przyciski pole wyboru i przycisków. Mogą być wbudowane funkcje grupy opcji przyciskami pole wyboru i `ON_UPDATE_COMMAND_UI`.  
  
 Wszystkie przyciski mapy bitowej na pasku narzędzi są pobierane z jednego mapy bitowej. Ta mapa bitowa musi zawierać jeden obraz lub symbolu dla każdego przycisku. Kolejność obrazów/symboli w pliku mapy bitowej jest zwykle takiej samej kolejności, który będzie rysowany na ekranie. (Można to zmienić za pomocą dostosowania interfejsów API.)  
  
 Każdy przycisk musi być taki sam rozmiar. Wartość domyślna to standardowa 24 x 22 piksele. Każdy obraz/symbolu musi mieć taki sam rozmiar, a musi być side-by-side w pliku mapy bitowej. Domyślny rozmiar obrazu/symbolu jest 16 x 15 pikseli. Na pasku narzędzi z przyciskami 10 (przy użyciu standardowych rozmiarów), należy więc mapę bitową 160 pikseli szerokości i wysokości 15 pikseli.  
  
 Każdy przycisk ma jeden i tylko jeden obraz/symbolu. Przycisk różne stany i style (na przykład naciśnięty, up, wyłączona w dół, wyłączona w dół i w nieokreślonej) algorithmically zostaną wygenerowane na podstawie jednego obrazu/symbolu. Teoretycznie można kolorów mapy bitowej ani DIB. Algorytm generowania inny przycisk stany działa najlepiej, jeśli oryginalnego obrazu jest odcieni szarości. Przyjrzyj się przycisków standardowym pasku narzędzi i clipart przycisku paska narzędzi w przykładowej ogólne MFC [CLIPART](../visual-cpp-samples.md) przykłady.  
  
 Kolory używane w pasku narzędzi są również zgodnie z zaleceniem Podręcznik projektowania aplikacji interfejsu systemu Windows. Kolory twarde nie są zakodowane i są zmieniane dynamicznie w odpowiedzi na dostosowaniem wprowadzanym przez użytkowników w Panelu sterowania.  
  
|Element|Wartości kolorów systemu Windows|Domyślne RGB|  
|----------|-------------------------|-----------------|  
|Tła paska narzędzi|**COLOR_BTNFACE**|RGB(192,192,192)|  
|Przyciski paska narzędzi góry/do lewej krawędzi.|**COLOR_BTNHIGHLIGHT**|RGB(255,255,255)|  
|Przyciski paska narzędzi bot/prawej krawędzi.|**COLOR_BTNSHADOW**|RGB(128,128,128)|  
  
 Ponadto przycisków paska mapy bitowej są ponownie pokolorowane tak, jakby były standardowych kontrolek przycisku systemu Windows. Ponowne kolorowanie ten występuje, gdy mapy bitowej jest ładowany z zasobów, a w odpowiedzi na zmianę w kolorów systemu w odpowiedzi na dostosowaniem wprowadzanym przez użytkowników w Panelu sterowania. Następujące kolorów mapy bitowej narzędzi będzie automatycznie klipu, powinny być używane z rozwagą. Jeśli nie chcesz, aby części z mapy bitowej ponownie pokolorowane, użyj kolor, który zbliżonego jedna z wartości RGB mapowane. Mapowanie odbywa się na podstawie wartości RGB dokładne.  
  
|Wartości RGB|Mapowanego dynamicznie wartość KOLORU|  
|---------------|------------------------------------|  
|RGB (000 000, 000)|COLOR_BTNTEXT|  
|RGB (128, 128, 128)|COLOR_BTNSHADOW|  
|RGB (192, 192, 192)|COLOR_BTNFACE|  
|RGB (255 255, 255)|COLOR_BTNHIGHLIGHT|  
  
 Odwołuje się do klasy [ctoolbar —](../mfc/reference/ctoolbar-class.md) *informacje dotyczące biblioteki klas* szczegółowe informacje o `CToolBar` tworzenia i dostosowywania interfejsów API. Większość Dostosowywanie pasków narzędzi należy zrobić przed narzędzi początkowo stają się widoczne.  
  
 Dostosowywanie interfejsów API może służyć do przycisku identyfikatory, style, Dostosuj szerokość rozdzielacza i obrazu/symbolu, który jest używany do działania przycisku. Domyślnie nie należy używać tych interfejsów API.  
  
## <a name="ccmdui-support-for-ctoolbar"></a>Ctoolbar — ccmdui — Obsługa  
 Sposób przycisków paska narzędzi są aktualizowane zawsze odbywa się za pośrednictwem `ON_UPDATE_COMMAND_UI` mechanizmu. Na czas bezczynności, wywoła pasek narzędzi `ON_UPDATE_COMMAND_UI` obsługi z poleceniem o identyfikatorze przycisku. `ON_UPDATE_COMMAND_UI` nie jest wywoływany dla separatorów, ale jest ona wywoływana dla przycisków i pola wyboru przycisków.  
  
 `ON_UPDATE_COMMAND_UI` Obsługi można wywołać:  
  
- **Włącz**: Aby włączyć lub wyłączyć przycisku. To działanie jest równie przycisków i pola wyboru przycisków.  
  
- `SetCheck`: Można ustawić stanu wyboru przycisku. To wywołanie dla przycisku paska narzędzi spowoduje wyłączenie w przycisk pola wyboru. `SetCheck` przyjmuje parametr, który może być 0 (nie jest zaznaczone), 1 (zaznaczone) lub 2 (nieokreślony)  
  
- `SetRadio`: Skrócona dla `SetCheck`.  
  
 Pole wyboru przyciski to przyciski pole wyboru "AUTOMATYCZNIE"; oznacza to gdy użytkownik naciśnie ich one natychmiast zmieni stan. Sprawdzane jest w stanie wyłączenia lub wciśnięte. Nie istnieje sposób interfejsu użytkownika wbudowanych zmienić przycisku do stanu "nieokreślony"; które muszą być wykonywane przez kod.  
  
 Dostosowywanie interfejsów API pozwoli zmienić stan przycisku paska narzędzi danego, najlepiej należy zmieniać te stany w `ON_UPDATE_COMMAND_UI` obsługi polecenia reprezentuje przycisk paska narzędzi. Należy pamiętać, że przetwarzanie w stanie bezczynności spowoduje zmianę stanu przycisków paska narzędzi z `ON_UPDATE_COMMAND_UI` obsługi, aby zmiany wprowadzone w tych stanów wprowadzane za pośrednictwem SetButtonStyle może zostać utracone po następnej bezczynności.  
  
 Przyciski paska narzędzi będzie wysyłać **WM_COMMAND** komunikaty, takie jak normalne przycisków lub elementów menu i są zazwyczaj obsługiwane przez `ON_COMMAND` obsługi w tej samej klasy, która zapewnia `ON_UPDATE_COMMAND_UI` obsługi.  
  
 Istnieją cztery narzędzi style przycisku (wartości TBBS_) używany do wyświetlania stany:  
  
-   TBBS_CHECKED: pole wyboru zostało zaznaczone obecnie (wyłączone).  
  
-   TBBS_INDETERMINATE: pole wyboru jest obecnie nieokreślony.  
  
-   TBBS_DISABLED: Przycisk jest obecnie wyłączona.  
  
-   TBBS_PRESSED: Obecnie naciśnięciu przycisku.  
  
 Sześć oficjalnego style przycisku Podręcznik projektowania aplikacji interfejsu systemu Windows są reprezentowane przez następujące wartości TBBS:  
  
-   Maksymalnie = 0  
  
-   Wskaźnik myszy w dół = TBBS_PRESSED (&#124; inny styl)  
  
-   Wyłączone = TBBS_DISABLED  
  
-   W dół = TBBS_CHECKED  
  
-   Dół wyłączone = TBBS_CHECKED &#124; TBBS_DISABLED  
  
-   Nieokreślony = TBBS_INDETERMINATE  
  
##  <a name="_mfcnotes_cdialogbar"></a> Cdialogbar —  
 Paska dialogowego jest pasek sterowania, który zawiera formanty standardowe systemu Windows. Go działa jak okna dialogowego, ponieważ zawiera formanty i obsługuje przełączania między nimi. On również działa jak okno dialogowe, gdyż używa do reprezentowania pasku szablonu okna dialogowego.  
  
 A `CDialogBar` służy do narzędzi podglądu wydruku, który zawiera standardowe formanty łącznik.  
  
 Przy użyciu `CDialogBar` podobnie jak przy użyciu `CFormView`. Należy zdefiniować szablonu okna dialogowego dla paska dialogowego i usunąć wszystkie style, z wyjątkiem **ws_child —**. Należy pamiętać, że okno dialogowe nie musi być widoczny.  
  
 Powiadomień dotyczących formantów dla `CDialogBar` zostaną wysłane do nadrzędnego pasek sterowania (podobnie jak przyciski paska narzędzi).  
  
## <a name="ccmdui-support-for-cdialogbar"></a>Cdialogbar — ccmdui — Obsługa  
 Przycisków paska dialogowego powinny być aktualizowane za pośrednictwem `ON_UPDATE_COMMAND_UI` mechanizm obsługi. W czasie bezczynności wywoła paska dialogowego `ON_UPDATE_COMMAND_UI` obsługi z poleceniem o identyfikatorze przycisków, które mają identyfikator > = 0x8000 (to znaczy w zakresie identyfikatory poleceń).  
  
 `ON_UPDATE_COMMAND_UI` Obsługi można wywołać:  
  
-   Włącz: aby Włącz lub Wyłącz przycisk.  
  
-   SetText: Aby zmienić tekst przycisku.  
  
 Dostosowywanie może odbywać się za pośrednictwem Menedżera okien standardowych interfejsów API.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

