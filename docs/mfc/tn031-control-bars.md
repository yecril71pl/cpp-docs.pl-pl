---
title: 'TN031: paski sterowania'
ms.date: 11/04/2016
f1_keywords:
- vc.controls.bars
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
ms.openlocfilehash: 37c3a15c281018260e65508dee3799ab0011dbfe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370305"
---
# <a name="tn031-control-bars"></a>TN031: paski sterowania

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

W tej notatce opisano klasy paska sterowania w MFC: ogólny [CControlBar](#_mfcnotes_ccontrolbar), [CStatusBar](#_mfcnotes_cstatusbar), [CToolBar](#_mfcnotes_ctoolbar), [CDialogBar](#_mfcnotes_cdialogbar)i `CDockBar`.

## <a name="ccontrolbar"></a><a name="_mfcnotes_ccontrolbar"></a>Ccontrolbar

A `ControlBar` jest `CWnd`klasą pochodną, która:

- Jest wyrównany do górnej lub dolnej części okna ramki.

- Mogą zawierać elementy podrzędne, które są formantami `CDialogBar`opartymi na`HWND` HWND (na przykład) lub nieopartymi na nich elementami (na przykład `CToolBar`, `CStatusBar`).

Paski sterowania obsługują dodatkowe style:

- CBRS_TOP (Domyślnie) przypiąć pasek sterowania do góry.

- CBRS_BOTTOM Przypiąć pasek sterowania do dołu.

- CBRS_NOALIGN Nie zmieniaj położenia paska sterowania, gdy element nadrzędny zmienia rozmiar.

Klasy pochodzące `CControlBar` z zapewnienia bardziej interesujących implementacji:

- `CStatusBar`Pasek stanu, elementy to okienka paska stanu zawierające tekst.

- `CToolBar`Pasek narzędzi, elementy są przyciskami mapy bitowej wyrównanymi w wierszu.

- `CDialogBar`Ramka przypominająca pasek narzędzi zawierająca standardowe formanty systemu Windows (utworzona na podstawie zasobu szablonu okna dialogowego).

- `CDockBar`Uogólniony obszar `CControlBar` dokowania dla innych obiektów pochodnych. Funkcje i zmienne określonego elementu członkowskiego dostępne w tej klasie mogą ulec zmianie w przyszłych wersjach.

Wszystkie obiekty/okna paska sterowania będą oknami podrzędnymi jakiegoś okna ramki nadrzędnej. Są one zwykle dodawane jako element równorzędny do obszaru klienta ramki (na przykład klienta MDI lub widoku). Identyfikator okna podrzędnego paska sterowania jest ważny. Domyślny układ paska sterowania działa tylko dla prętów sterujących o identyfikatorach w zakresie AFX_IDW_CONTROLBAR_FIRST do AFX_IDW_CONTROLBAR_LAST. Należy zauważyć, że mimo że istnieje zakres 256 identyfikatorów paska sterowania, pierwsze 32 z tych identyfikatorów paska sterowania są specjalne, ponieważ są one bezpośrednio obsługiwane przez architekturę podglądu wydruku.

Klasa `CControlBar` zapewnia standardową implementację dla:

- Wyrównywanie paska sterowania do górnej, dolnej lub po drugiej stronie ramki.

- Przydzielanie tablic elementów kontrolnych.

- Wspieranie implementacji klas pochodnych.

Obiekty paska sterowania języka C++ będą `CFrameWnd` zwykle osadzane jako elementy członkowskie klasy `HWND` pochodnej i zostaną wyczyszczone, gdy element nadrzędny i obiekt zostaną zniszczone. Jeśli chcesz przydzielić obiekt paska sterowania na stercie, możesz po prostu ustawić *m_bAutoDestruct* element członkowski na `HWND` **TRUE,** aby pasek sterowania " usunąć**to**" po zniszczeniu.

> [!NOTE]
> Jeśli utworzysz `CControlBar`własną klasę pochodną, a nie jedną z klas pochodnych MFC, taką `CStatusBar`jak , `CToolBar`lub `CDialogBar`, musisz ustawić *m_dwStyle* element członkowski danych. Można to zrobić w zastąpiona: `Create`

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

**Algorytm układu paska sterowania**

Algorytm układu paska sterowania jest bardzo prosty. Okno ramki wysyła komunikat WM_SIZEPARENT do wszystkich wiązek podrzędnych w zakresie paska sterowania. Wraz z tym komunikatem przechodzi wskaźnik do prostokąta klienta rodzica. Ta wiadomość jest wysyłana do dzieci w kolejności Z. Dzieci paski kontroli używają tych informacji do pozycjonowanie siebie i zmniejszenia rozmiaru obszaru klienta nadrzędnego. Końcowy prostokąt, który jest pozostawiony dla normalnego obszaru klienta (mniej pasków sterowania) jest używany do pozycjonowanie głównego okna klienta (zwykle klienta MDI, okna widoku lub rozdzielacza).

Zobacz `CWnd::RepositionBars` `CFrameWnd::RecalcLayout` i więcej szczegółów.

Prywatne wiadomości mfc systemu Windows, w tym WM_SIZEPARENT, są udokumentowane w [notatce technicznej 24](../mfc/tn024-mfc-defined-messages-and-resources.md).

## <a name="cstatusbar"></a><a name="_mfcnotes_cstatusbar"></a>Cstatusbar

Pasek stanu to pasek sterowania zawierający wiersz okienek wyjściowych tekstu. Istnieją dwa typowe sposoby używania okienek danych wyjściowych tekstu:

- Jako wiersz wiadomości

     (na przykład standardowy wiersz komunikatu pomocy menu). Zazwyczaj są one dostępne za pomocą

- Jako wskaźniki stanu

     (na przykład wskaźniki WPR, NUM i SCRL). Są one zwykle dostępne za pomocą identyfikatora ciągu/polecenia.

Czcionka paska stanu to 10-punktowy ms sans serif (podyktowany przewodnikiem projektowania aplikacji interfejsu systemu Windows lub maperami czcionek najlepiej dopasowanym do 10-punktowej szwajcarskiej czcionki proporcjonalnej). W niektórych wersjach systemu Windows, takich jak wersja japońska, wybrane czcionki są różne.

Kolory używane na pasku stanu są również zgodne z zaleceniem Przewodnika po projektowaniu aplikacji interfejsu systemu Windows. Kolory te nie są zakodowane na twardo i są zmieniane dynamicznie w odpowiedzi na dostosowanie użytkownika w Panelu sterowania.

|Element|Wartość COLOR systemu Windows|Domyślna wartość RGB|
|----------|-------------------------|-----------------|
|Tło paska stanu|COLOR_BTNFACE|RGB(192, 192, 192)|
|Tekst paska stanu|COLOR_BTNTEXT|RGB(000, 000, 000)|
|Pasek stanu górne/lewe krawędzie|COLOR_BTNHIGHLIGHT|RGB(255, 255, 255)|
|Pasek stanu bot/prawe krawędzie|COLOR_BTNSHADOW|RGB(128, 128, 128)|

**Obsługa CCmdUI dla CStatusBar**

Sposób, w jaki wskaźniki są zwykle aktualizowane, odbywa się za pośrednictwem mechanizmu ON_UPDATE_COMMAND_UI. W czasie bezczynności pasek stanu wywoła program obsługi ON_UPDATE_COMMAND_UI z identyfikatorem ciągu okienka wskaźnika.

Program obsługi ON_UPDATE_COMMAND_UI może wywołać:

- `Enable`: Aby włączyć lub wyłączyć okienko. Wyłączone okienko wygląda dokładnie tak, jak włączone okienko, ale tekst jest niewidoczny (czyli wyłącza wskaźnik tekstu).

- `SetText`: Aby zmienić tekst. Należy zachować ostrożność, jeśli używasz tego, ponieważ okienko nie będzie automatycznie zmienić rozmiar.

Szczegółowe informacje na temat `CStatusBar` tworzenia i dostosowywania interfejsów API można znaleźć w instrukcji [CStatusBar](../mfc/reference/cstatusbar-class.md) klasy w *bibliotece klas.* Większość dostosowywania pasków stanu powinna być wykonywana, zanim pasek stanu zostanie początkowo widoczny.

Pasek stanu obsługuje tylko jedno rozciągliwe okienko, zwykle pierwsze okienko. Rozmiar tego okienka jest naprawdę minimalny rozmiar. Jeśli pasek stanu jest większy niż minimalny rozmiar wszystkich okienek, wszelkie dodatkowe szerokości zostaną podane do rozciągliwego okienka. Domyślna aplikacja z paskiem stanu ma wyrównane do prawej wskaźniki dla CAP, NUM i SCRL, ponieważ pierwsze okienko jest rozciągliwe.

## <a name="ctoolbar"></a><a name="_mfcnotes_ctoolbar"></a>Ctoolbar

Pasek narzędzi to pasek sterowania z wierszem przycisków mapy bitowej, które mogą zawierać separatory. Obsługiwane są dwa style przycisków: przyciski i przyciski pól wyboru. Funkcje grupy radiowej można budować za pomocą przycisków pola wyboru i ON_UPDATE_COMMAND_UI.

Wszystkie przyciski bitmapy na pasku narzędzi są pobierane z jednej mapy bitowej. Ta mapa bitowa musi zawierać jeden obraz lub glif dla każdego przycisku. Zazwyczaj kolejność obrazów/glifów na mapie bitowej jest taka sama, jaka zostanie narysowana na ekranie. (Można to zmienić za pomocą interfejsów API dostosowywania).

Każdy przycisk musi mieć ten sam rozmiar. Wartość domyślna to standardowa 24x22 pikseli. Każdy obraz/glif musi mieć ten sam rozmiar i musi być obok siebie w mapie bitowej. Domyślny rozmiar obrazu/glifów to 16x15 pikseli. W związku z tym w przypadku paska narzędzi z 10 przyciskami (przy użyciu standardowych rozmiarów) potrzebna jest mapa bitowa o szerokości 160 pikseli i wysokości 15 pikseli.

Każdy przycisk ma jeden i tylko jeden obraz / glif. Różne stany i style przycisków (na przykład wciśnięty, w górę, w dół, wyłączone, wyłączone w dół, nieokreślony) są generowane algorytmicznie z tego jednego obrazu/glifu. Teoretycznie można użyć dowolnej kolorowej mapy bitowej lub DIB. Algorytm generowania różnych stanów przycisków działa najlepiej, jeśli oryginalny obraz jest odcieniami szarości. Spójrz na standardowe przyciski paska narzędzi i clipart przycisku paska narzędzi podane w przykładzie MFC Ogólne [CLIPART](../overview/visual-cpp-samples.md) przykłady.

Kolory używane na pasku narzędzi są również zgodne z zaleceniem Przewodnika po projektowaniu aplikacji interfejsu systemu Windows. Kolory te nie są zakodowane na twardo i są zmieniane dynamicznie w odpowiedzi na dostosowanie użytkownika w Panelu sterowania.

|Element|Wartość COLOR systemu Windows|Domyślna wartość RGB|
|----------|-------------------------|-----------------|
|Tło paska narzędzi|COLOR_BTNFACE|RGB(192,192,192)|
|Przyciski paska narzędzi u góry/do lewej krawędzi|COLOR_BTNHIGHLIGHT|RGB(255,255,255)|
|Przyciski paska narzędzi bot/prawe krawędzie|COLOR_BTNSHADOW|RGB(128,128,128)|

Ponadto przyciski mapy bitowej paska narzędzi są ponownie kolorowane tak, jakby były standardowymi formantami przycisków systemu Windows. To ponowne kolorowanie występuje, gdy mapa bitowa jest ładowana z zasobu i w odpowiedzi na zmianę kolorów systemowych w odpowiedzi na dostosowanie użytkownika w Panelu sterowania. Następujące kolory na mapie bitowej paska narzędzi zostaną automatycznie ponownie pokolorowane, dlatego należy ich używać ostrożnie. Jeśli nie chcesz, aby część mapy bitowej została ponownie pokolorowana, użyj koloru, który ściśle przybliża jedną z mapowanych wartości RGB. Mapowanie odbywa się na podstawie dokładnych wartości RGB.

|Wartość RGB|Dynamicznie mapowana wartość COLOR|
|---------------|------------------------------------|
|RGB(000, 000, 000)|COLOR_BTNTEXT|
|RGB(128, 128, 128)|COLOR_BTNSHADOW|
|RGB(192, 192, 192)|COLOR_BTNFACE|
|RGB(255, 255, 255)|COLOR_BTNHIGHLIGHT|

Zobacz klasy [CToolBar](../mfc/reference/ctoolbar-class.md) *odwołanie biblioteki klas, aby* uzyskać szczegółowe informacje na `CToolBar` temat tworzenia i dostosowywania interfejsów API. Większość dostosowywania pasków narzędzi powinna być wykonana, zanim pasek narzędzi zostanie początkowo widoczny.

Interfejsy API dostosowywania mogą być używane do dostosowywania identyfikatorów przycisków, stylów, szerokości dystansu i obrazu/glifu, który jest używany do tego przycisku. Domyślnie nie trzeba używać tych interfejsów API.

## <a name="ccmdui-support-for-ctoolbar"></a>Obsługa CCmdUI dla CToolBar

Sposób, w jaki przyciski paska narzędzi są zawsze aktualizowane, odbywa się za pośrednictwem mechanizmu ON_UPDATE_COMMAND_UI. W czasie bezczynności pasek narzędzi wywoła program obsługi ON_UPDATE_COMMAND_UI z identyfikatorem polecenia tego przycisku. ON_UPDATE_COMMAND_UI nie jest wywoływana dla separatorów, ale jest wywoływana dla przycisków i przycisków pola wyboru.

Program obsługi ON_UPDATE_COMMAND_UI może wywołać:

- `Enable`: Aby włączyć lub wyłączyć przycisk. Działa to jednakowo w przypadku przycisków i przycisków pól wyboru.

- `SetCheck`: Aby ustawić stan wyboru przycisku. Wywołanie tego przycisku paska narzędzi spowoduje przekształcenie go w przycisk pola wyboru. `SetCheck`przyjmuje parametr, który może być 0 (nie zaznaczone), 1 (sprawdzone) lub 2 (nieokreślony)

- `SetRadio`: Skrót `SetCheck`do .

Przyciski pola wyboru są przyciskami pola wyboru "AUTO"; oznacza to, że gdy użytkownik naciśnie je natychmiast zmieni stan. Sprawdzany jest stan w dół lub w depresji. Nie ma wbudowanego interfejsu użytkownika sposób, aby zmienić przycisk w stanie "nieokreślony"; które muszą być wykonane za pomocą kodu.

Interfejsy API dostosowywania umożliwiają zmianę stanu danego przycisku paska narzędzi, najlepiej należy zmienić te stany w programie obsługi ON_UPDATE_COMMAND_UI dla polecenia, które reprezentuje przycisk paska narzędzi. Pamiętaj, że bezczynne przetwarzanie zmieni stan przycisków paska narzędzi za pomocą ON_UPDATE_COMMAND_UI obsługi, więc wszelkie zmiany w tych stanach wprowadzone za pośrednictwem SetButtonStyle mogą zostać utracone po następnym bezczynności.

Przyciski paska narzędzi będą wysyłać WM_COMMAND wiadomości, takich jak normalne przyciski lub elementy menu i są zwykle obsługiwane przez program obsługi ON_COMMAND w tej samej klasie, która zapewnia ON_UPDATE_COMMAND_UI obsługi.

Istnieją cztery style przycisków paska narzędzi (TBBS_ wartości) używane w stanach wyświetlania:

- TBBS_CHECKED: Pole wyboru jest aktualnie zaznaczone (w dół).

- TBBS_INDETERMINATE: Pole wyboru jest obecnie nieokreślone.

- TBBS_DISABLED: Przycisk jest obecnie wyłączony.

- TBBS_PRESSED: Przycisk jest aktualnie naciśnięty.

Sześć oficjalnych stylów przycisków przewodnika po projektowaniu aplikacji interfejsu systemu Windows jest reprezentowanych przez następujące wartości TBBS:

- W górę = 0

- Mouse Down = TBBS_PRESSED (&#124; inny styl)

- Wyłączone = TBBS_DISABLED

- W dół = TBBS_CHECKED

- Wyłącz wyłączono = TBBS_CHECKED TBBS_DISABLED &#124;

- Nieokreślony = TBBS_INDETERMINATE

## <a name="cdialogbar"></a><a name="_mfcnotes_cdialogbar"></a>Cdialogbar

Pasek dialogowy to pasek sterowania zawierający standardowe formanty systemu Windows. Działa jak okno dialogowe, ponieważ zawiera formanty i obsługuje tabulacji między nimi. Działa również jak okno dialogowe, ponieważ używa szablonu okna dialogowego do reprezentowania paska.

A `CDialogBar` jest używany dla paska narzędzi podglądu wydruku, który zawiera standardowe kontrolki przycisku.

Korzystanie `CDialogBar` z jest `CFormView`jak przy użyciu . Należy zdefiniować szablon okna dialogowego dla paska dialogowego i usunąć wszystkie style z wyjątkiem WS_CHILD. Należy zauważyć, że okno dialogowe nie może być widoczne.

Powiadomienia sterujące dla `CDialogBar` a zostaną wysłane do nadrzędnego paska sterowania (podobnie jak przyciski paska narzędzi).

## <a name="ccmdui-support-for-cdialogbar"></a>Obsługa CCmdUI dla CDialogBar

Przyciski paska dialogowego powinny być aktualizowane za pomocą mechanizmu obsługi ON_UPDATE_COMMAND_UI. W czasie bezczynności pasek dialogowy wywoła program obsługi ON_UPDATE_COMMAND_UI z identyfikatorem polecenia wszystkich przycisków, które mają identyfikator >= 0x8000 (czyli w zakresie identyfikatorów poleceń).

Program obsługi ON_UPDATE_COMMAND_UI może wywołać:

- Włącz: aby włączyć lub wyłączyć przycisk.

- SetText: aby zmienić tekst przycisku.

Dostosowywanie można wykonać za pomocą standardowych interfejsów API menedżera okien.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
