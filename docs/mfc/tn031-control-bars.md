---
title: 'TN031: Paski sterowania'
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
ms.openlocfilehash: 39309408c6d1fc6cbb4223eda22c511865f14498
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58772517"
---
# <a name="tn031-control-bars"></a>TN031: Paski sterowania

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisuje klasy pasków sterowania w MFC: Ogólne [CControlBar](#_mfcnotes_ccontrolbar), [CStatusBar](#_mfcnotes_cstatusbar), [CToolBar](#_mfcnotes_ctoolbar), [CDialogBar](#_mfcnotes_cdialogbar)i `CDockBar`.

## <a name="_mfcnotes_ccontrolbar"></a> CControlBar

A `ControlBar` jest `CWnd`-pochodne klasy, które:

- Jest wyrównany do góry lub u dołu okna ramki.

- Może zawierać elementy podrzędne, które są albo kontrolę opartą na HWND (na przykład `CDialogBar`) lub innych niż-`HWND` na podstawie elementów (na przykład `CToolBar`, `CStatusBar`).

Paski sterowania obsługują dodatkowe style:

- Kod pin CBRS_TOP (ustawienie domyślne) pasek sterowania do góry.

- Kod Pin CBRS_BOTTOM pasek sterowania do dołu.

- Nie należy CBRS_NOALIGN zmienić położenie paska sterowania, gdy zmienia rozmiar obiektu nadrzędnego.

Klasy pochodne `CControlBar` dostarczać implementacje bardziej interesująca:

- `CStatusBar` Pasek stanu, są elementy zawierające tekst okienka paska stanu.

- `CToolBar` Pasek narzędzi, elementy są wyrównane w wierszu przyciski z mapami.

- `CDialogBar` Ramka pasek narzędzi, zawierającą standardowy system windows formantów (utworzone na podstawie zasobu szablonu okna dialogowego).

- `CDockBar` Uogólniony obszar dokowania dla innych `CControlBar` obiektami wywodzącymi. Określonych funkcji elementów członkowskich i zmienne dostępne w tej klasie mogą ulec zmianie w przyszłych wersjach.

Wszystkie kontrolki paska obiektów/system windows będzie okienka podrzędne dla niektórych nadrzędnej ramki okna. Są one zwykle dodawane jako element równorzędny do obszaru klienta ramki (na przykład klienta MDI lub widoku). Ważne jest identyfikator okna elementu podrzędnego paska sterowania. Domyślny układ paska sterowania działa tylko w przypadku paski sterowania z identyfikatorami w zakresie AFX_IDW_CONTROLBAR_FIRST do AFX_IDW_CONTROLBAR_LAST. Należy pamiętać, że nawet jeśli istnieje szereg kontroli 256 paska identyfikatorów, pierwsze 32 te pasek sterowania identyfikatory są specjalne, ponieważ są bezpośrednio obsługiwane przez architektura podglądu wydruku.

`CControlBar` Klasy zapewnia standardową implementację dla:

- Wyrównywanie pasek sterowania do górnej, dolnej lub po obu stronach ramki.

- Przydzielanie kontroli elementów tablic.

- Obsługa wdrażania w klasach pochodnych.

Obiekty pasek sterowania C++ zazwyczaj zostanie osadzony jako elementy członkowskie `CFrameWnd` klasę pochodną i zostaną wyczyszczone po nadrzędnej `HWND` i obiektu są niszczone. Jeśli musisz przydzielić obiektu pasek sterowania, na stosie, można po prostu ustawić *m_bAutoDestruct* członka do **TRUE** aby pasek sterowania "**usunąć ten**" podczas `HWND` zostanie zniszczony.

> [!NOTE]
>  Jeśli tworzysz własny `CControlBar`-pochodne klasy, a nie przy użyciu jednej z biblioteki MFC pochodne klasy, takie jak `CStatusBar`, `CToolBar`, lub `CDialogBar`, musisz ustawić *m_dwStyle* element członkowski danych. Można to zrobić w zastępowania metody `Create`:

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

**Algorytm Układ paska sterowania**

Algorytm Układ paska sterowania jest bardzo proste. Okno ramowe wysyła komunikat WM_SIZEPARENT do wszystkich elementów podrzędnych w zakresie paska sterowania. Wraz z ten komunikat jest przekazywany wskaźnik do elementu nadrzędnego jego klienta. Ta wiadomość jest wysyłana do elementów podrzędnych w porządku osi Z. Elementy podrzędne pasek sterowania dzięki tym informacjom pozycjonują się i Zmniejsz rozmiar obszaru klienckiego elementu nadrzędnego. Końcowe prostokąt, który pozostanie do obszaru klienckiego normalny (mniej pasków sterowania) jest używany do położenie okna głównego klienta (zazwyczaj klienta, widoku lub rozdzielacz okna MDI).

Zobacz `CWnd::RepositionBars` i `CFrameWnd::RecalcLayout` Aby uzyskać więcej informacji.

MFC prywatnej Windows komunikaty, w tym WM_SIZEPARENT, są udokumentowane w artykule [techniczne 24 Uwaga](../mfc/tn024-mfc-defined-messages-and-resources.md).

## <a name="_mfcnotes_cstatusbar"></a>  CStatusBar

Pasek stanu jest pasek sterowania, który zawiera wiersz tekstu wyjściowego okienka. Istnieją dwie typowe sposoby korzystania z okienka danych wyjściowych tekst:

- Jako wiersz wiadomości

     (na przykład standardowe menu Pomoc wiersz wiadomości). Te są zwykle dostępne przez 0 na podstawie indeksowane

- Jako wskaźniki stanu

     (na przykład limit, liczba i SCRL wskaźniki). Te są zwykle dostępne za pomocą polecenia/ciągu identyfikatora.

Czcionka na pasek stanu jest 10-punktowy MS Sans Serif (podyktowanej Podręcznik projektowania aplikacji interfejsu Windows lub czcionki liczby maperów najlepsze dopasowanie 10-punktowy szwajcarski czcionek proporcjonalnych). W niektórych wersjach systemu Windows, takie jak wersja japońska czcionek zaznaczonych różnią się.

Kolory używane w pasku stanu są również zgodne z zaleceniem przewodnik projektowania aplikacji interfejsu programu Windows. Te kolory nie są kodowane trudne, a zostaną zmienione dynamicznie w odpowiedzi na dostosowywanie użytkownika w Panelu sterowania.

|Element|Wartość KOLORU Windows|Domyślne RGB|
|----------|-------------------------|-----------------|
|Tło paska stanu|COLOR_BTNFACE|RGB(192, 192, 192)|
|Tekst paska stanu|COLOR_BTNTEXT|RGB (000 000, 000)|
|Góra/lewo krawędziach — pasek stanu|COLOR_BTNHIGHLIGHT|RGB(255, 255, 255)|
|Bot/prawej krawędzi — pasek stanu|COLOR_BTNSHADOW|RGB (128, 128, 128)|

**CCmdUI obsługę CStatusBar**

Sposób, w jaki wskaźniki są zazwyczaj aktualizowane jest mechanizm ON_UPDATE_COMMAND_UI. Na czas bezczynności na pasku stanu będzie wywoływać procedury obsługi ON_UPDATE_COMMAND_UI o identyfikatorze ciąg w okienku wskaźnika.

Można wywołać procedury obsługi ON_UPDATE_COMMAND_UI:

- `Enable`: Aby włączyć lub wyłączyć okienka. Okienko wyłączone wygląda tak samo jak okienko włączone, ale tekst jest niewidoczne (czyli wyłącza wskaźnik).

- `SetText`: Aby zmienić tekst. Należy zachować ostrożność, korzystając z tego, ponieważ nie będzie automatycznie rozmiar okienka.

Można znaleźć klasy [CStatusBar](../mfc/reference/cstatusbar-class.md) w *odwołanie do biblioteki klas* szczegółowe informacje na temat `CStatusBar` tworzenia i dostosowywania interfejsów API. Większość dostosowywania pasków stanu należy przeprowadzić przed wykonaniem na pasku stanu jest początkowo widoczne.

Na pasku stanu obsługuje tylko jedno okienko stretchy zazwyczaj pierwszą okienko. Rozmiar okienka naprawdę jest minimalny rozmiar. Jeśli na pasku stanu jest większy niż minimalny rozmiar wszystkich okienek, wszelkie dodatkową szerokość zostanie przydzielony do okienka stretchy. Domyślną aplikację przy użyciu paska stanu ma wyrównany do prawej wskaźniki limit, liczba i SCRL, ponieważ pierwszy okienko jest stretchy.

## <a name="_mfcnotes_ctoolbar"></a>  CToolBar

Pasek narzędzi jest pasek sterowania z wiersz przycisków mapy bitowej, które mogą zawierać separatorów. Obsługiwane są dwa style przyciski: przyciski pole wyboru i przyciski. Mogą być wbudowane funkcje grupy radio z przyciskami pola wyboru i ON_UPDATE_COMMAND_UI.

Wszystkie przyciski mapy bitowej na pasku narzędzi są pobierane z jednego mapy bitowej. Ta mapa bitowa musi zawierać jeden obraz lub symbol dla każdego przycisku. Zazwyczaj kolejność obrazów/symbole w mapie bitowej jest tej samej kolejności, w których będą rysowane na ekranie. (Można to zmienić przy użyciu dostosowanych interfejsów API.)

Każdy przycisk musi być taki sam rozmiar. Wartość domyślna to standardowa 24 x 22 piksele. Każdy obraz/glifu musi być taki sam rozmiar i musi być side-by-side w mapie bitowej. Domyślny rozmiar obrazu/glifu to 16 x 15 pikseli. W związku z tym pasek narzędzi za pomocą przycisków 10 (przy użyciu standardowych rozmiarów maszyn wirtualnych), należy mapy bitowej, który jest 160 pikseli szerokości i wysokości 15 pikseli.

Każdy przycisk ma jeden i tylko jeden obraz/glifu. Inny przycisk stanów i style (na przykład naciśnięty w górę, w dół, wyłączona, wyłączona w dół i w nieokreślonej) algorithmically są generowane na podstawie jednego obrazu/glifu. Teoretycznie można kolorów mapy bitowej ani DIB. Algorytm generowania inny przycisk stanów działa najlepiej przypadku oryginalny obraz na odcienie szarości. Przyjrzyj się przycisków na pasku narzędzi Standardowy i clipart przycisku paska narzędzi, podano w przykładzie ogólne MFC [CLIPART](../overview/visual-cpp-samples.md) przykłady.

Kolorów używanych na pasku narzędzi są również zgodne z zaleceniem Podręcznik projektowania aplikacji interfejsu Windows. Te kolory nie są kodowane trudne, a zostaną zmienione dynamicznie w odpowiedzi na dostosowywanie użytkownika w Panelu sterowania.

|Element|Wartość KOLORU Windows|Domyślne RGB|
|----------|-------------------------|-----------------|
|Tła paska narzędzi|COLOR_BTNFACE|RGB(192,192,192)|
|Góra/lewo krawędzie przyciski paska narzędzi|COLOR_BTNHIGHLIGHT|RGB(255,255,255)|
|Przyciski paska narzędzi bot/prawej krawędzi|COLOR_BTNSHADOW|RGB(128,128,128)|

Ponadto przyciski z mapami narzędzi są ponownie pokolorowane tak, jakby były standardowych kontrolek przycisku Windows. Ponowne kolorowanie ten występuje, gdy mapy bitowej jest ładowany z zasobu, a w odpowiedzi na zmianę w kolory systemowe w odpowiedzi na dostosowywanie użytkownika w Panelu sterowania. Następujących kolorów mapy bitowej narzędzi będzie klipu automatycznie, więc należy jej używać ostrożnie. Jeśli użytkownik nie chce mieć części Twojej mapy bitowej ponownie pokolorowane, użyj kolor, który zbliżony jeden mapowane wartości RGB. Mapowanie jest wykonywane na podstawie dokładne wartości RGB.

|Wartość RGB|Dynamicznie mapowaną wartość KOLORU|
|---------------|------------------------------------|
|RGB (000 000, 000)|COLOR_BTNTEXT|
|RGB (128, 128, 128)|COLOR_BTNSHADOW|
|RGB(192, 192, 192)|COLOR_BTNFACE|
|RGB(255, 255, 255)|COLOR_BTNHIGHLIGHT|

Można znaleźć klasy [CToolBar](../mfc/reference/ctoolbar-class.md) *odwołanie do biblioteki klas* szczegółowe informacje na temat `CToolBar` tworzenia i dostosowywania interfejsów API. Powinna być podejmowana większość dostosowywania pasków narzędzi, przed wykonaniem pasek narzędzi jest początkowo widoczne.

Dostosowywanie interfejsów API można dostosować przycisk identyfikatorów, style, szerokość rozdzielacza i które obrazu/glifu służy do działania przycisku. Domyślnie jest konieczne korzystanie z tych interfejsów API.

## <a name="ccmdui-support-for-ctoolbar"></a>CCmdUI obsługę CToolBar

Sposób, w jaki przycisków na pasku narzędzi są aktualizowane zawsze jest za pośrednictwem mechanizmu ON_UPDATE_COMMAND_UI. Na czas bezczynności pasek narzędzi będzie wywoływać procedury obsługi ON_UPDATE_COMMAND_UI, identyfikatorem polecenia tego przycisku. ON_UPDATE_COMMAND_UI nie jest wywoływana dla separatory, ale jest ona wywoływana dla przycisków pole wyboru i przyciski.

Można wywołać procedury obsługi ON_UPDATE_COMMAND_UI:

- `Enable`: Aby włączyć lub wyłączyć przycisk. Ta funkcja działa równie przycisków pole wyboru i przyciski.

- `SetCheck`: Aby ustawić stan wyboru przycisku. To wywołanie dla przycisku kontrolki toolbar spowoduje wyłączenie w przycisk pola wyboru. `SetCheck` przyjmuje parametr, który może być 0 (niezaznaczone), 1 (zaznaczony) lub 2 (nieokreślone)

- `SetRadio`: Skrócona forma funkcji `SetCheck`.

Pole wyboru przyciski są przyciski pole wyboru "AUTOMATYCZNIE"; oznacza to gdy użytkownik naciśnie im one natychmiast zmianą stanu. Sprawdzane jest wyłączony lub z włączonym stanem. Nie istnieje sposób interfejsu użytkownika wbudowanych można zmienić przycisku do stanu "nieokreślone"; który musi odbywać się za pomocą kodu.

Dostosowywanie interfejsów API pozwoli zmienić stan przycisku paska narzędzi danego, najlepiej należy zmienić tych stanów w obsłudze ON_UPDATE_COMMAND_UI dla polecenia, które reprezentuje przycisk na pasku narzędzi. Należy pamiętać, że przetwarzanie w stanie bezczynności spowoduje zmiany stanu przycisków paska narzędzi z programem obsługi ON_UPDATE_COMMAND_UI, dzięki czemu zmiany wprowadzone w tych stanów za pośrednictwem SetButtonStyle może zostać utracone po następnym bezczynności.

Wm_command — komunikaty, takie jak normalne przycisków lub elementy menu i zwykle są obsługiwane przez program obsługi ON_COMMAND w tej samej klasy, który zawiera program obsługi ON_UPDATE_COMMAND_UI, będzie wysyłać przycisków paska narzędzi.

Istnieją cztery narzędzi style przycisku (TBBS_ wartości) używane do stanów wyświetlania:

- TBBS_CHECKED:   Obecnie jest zaznaczone pole wyboru (w dół).

- TBBS_INDETERMINATE:   Pole wyboru jest obecnie nieokreślony.

- TBBS_DISABLED:   Przycisk jest obecnie wyłączona.

- TBBS_PRESSED:   Obecnie naciśnięciu przycisku.

Sześć style przycisku oficjalny przewodnik projektowania aplikacji interfejsu Windows są reprezentowane przez następujące wartości TBBS:

- Nawet = 0

- Myszy w dół = TBBS_PRESSED (&#124; innych stylu)

- Wyłączone = TBBS_DISABLED

- W dół = TBBS_CHECKED

- Dół wyłączone = TBBS_CHECKED &#124; TBBS_DISABLED

- Nieokreślony = TBBS_INDETERMINATE

##  <a name="_mfcnotes_cdialogbar"></a> CDialogBar

Pasek dialogowy jest pasek sterowania, który zawiera standardowe formanty Windows. Jego działa jak okna dialogowego, ponieważ zawiera formanty i obsługuje przełączania między nimi. Również działa podobnie jak okna dialogowego, gdyż używa szablonu okna dialogowego do reprezentowania na pasku.

A `CDialogBar` służy do narzędzi podglądu wydruku, który zawiera standardowe mapami kontrolki.

Za pomocą `CDialogBar` podobnie jak przy użyciu `CFormView`. Należy zdefiniować szablonu okna dialogowego na Pasek dialogowy i Usuń wszystkie style, z wyjątkiem WS_CHILD. Należy pamiętać, że okno dialogowe nie mogą być widoczne.

Powiadomień dotyczących formantu karty dla `CDialogBar` będą wysyłane do nadrzędnego pasek sterowania (podobnie jak przyciski paska narzędzi).

## <a name="ccmdui-support-for-cdialogbar"></a>CCmdUI obsługę CDialogBar

Przyciski paska dialogowego powinny być aktualizowane za pośrednictwem mechanizmu obsługi ON_UPDATE_COMMAND_UI. W czasie bezczynności, Pasek dialogowy wywoła procedurę obsługi ON_UPDATE_COMMAND_UI, identyfikatorem polecenia przycisków, które mają identyfikator > = 0x8000 (czyli w zakresie identyfikatory poleceń).

Można wywołać procedury obsługi ON_UPDATE_COMMAND_UI:

- Włącz: Aby włączyć lub wyłączyć przycisk.

- SetText —: Aby zmienić tekst przycisku.

Dostosowywanie może odbywać się za pośrednictwem Menedżera okien standardowych interfejsów API.

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
