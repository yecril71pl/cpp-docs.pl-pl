---
title: 'TN025: tworzenie dokumentów, widoków i ramek'
ms.date: 11/04/2016
f1_keywords:
- vc.creation
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
ms.openlocfilehash: aa8bc305848ce95e0b5bfef1ac6785b18bc84015
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50634762"
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025: tworzenie dokumentów, widoków i ramek

> [!NOTE]
>  Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisuje problemy z tworzeniem i własność WinApps, DocTemplates, dokumentów, ramek i widokami.

## <a name="winapp"></a>Aplikacji systemu Windows

Istnieje `CWinApp` obiektu w systemie.

Jest statycznie skonstruowany i inicjowane za wykazanie wewnętrzną implementację `WinMain`. Muszą pochodzić od `CWinApp` do żadnych użytecznych czynności (wyjątek: biblioteki DLL rozszerzeń MFC nie powinny mieć `CWinApp` wystąpienia — inicjowanie odbywa się w `DllMain` zamiast).

Ten `CWinApp` obiekt posiada listę szablonów dokumentów ( `CPtrList`). Istnieje co najmniej jeden szablon dokumentu, na aplikację. DocTemplates zwykle są załadowane z pliku zasobów (czyli tablicy ciągów) w `CWinApp::InitInstance`.

```
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```

Ten `CWinApp` obiektu jest właścicielem wszystkich okien ramowych w aplikacji. W oknie głównym ramki aplikacji powinny być przechowywane w `CWinApp::m_pMainWnd`; zazwyczaj ustawiony *elementu m_pMainWnd* w `InitInstance` wdrożenia, jeśli nie wybierzesz AppWizard zrobił dla Ciebie. Dla interfejsu pojedynczego dokumentu (SDI) jest to jedna `CFrameWnd` służy jako okno ramowe aplikacji głównej, a także tylko okna ramki dokumentu. W przypadku interfejsu wielu dokumentów (MDI) jest ramek MDI (klasy `CMDIFrameWnd`) który służy jako okno ramowe aplikacji głównej, która zawiera wszystkie podrzędne `CFrameWnd`s. Każde okno podrzędne jest klasą `CMDIChildWnd` (pochodną `CFrameWnd`) i służy jako jeden z potencjalnie wiele okien ramowych dokumentu.

## <a name="doctemplates"></a>DocTemplates

`CDocTemplate` Twórcy i Menedżera dokumentów. Dokumenty, które tworzy jego właścicielem. Jeśli aplikacja korzysta z podejścia opartego na zasobach, opisane poniżej, trzeba będzie ją nie pochodzi od `CDocTemplate`.

Dla aplikacji interfejsu SDI klasy `CSingleDocTemplate` śledzi informacje o co otwartego dokumentu. Dla aplikacji MDI, klasa `CMultiDocTemplate` przechowuje listę ( `CPtrList`) z aktualnie otwarte dokumenty tworzone na podstawie tego szablonu. `CDocTemplate::AddDocument` i `CDocTemplate::RemoveDocument` zapewnia wirtualna elementu członkowskiego funkcji dodawania lub usuwania dokumentu z szablonu. `CDocTemplate` jest zaprzyjaźniona z `CDocument` więc możemy ustawić chronionego `CDocument::m_pDocTemplate` wskaźnik Wstecz, aby wskazać szablonu dokumentu, który utworzył dokument.

`CWinApp` obsługuje domyślnie `OnFileOpen` wdrażania, który z kolei wysyła kwerendy do wszystkich szablonów dokumentów. Implementacja obejmuje wyszukiwanie już otwarte dokumenty i podejmowania decyzji o jakiego formatu, aby otworzyć nowe dokumenty w.

`CDocTemplate` zarządza powiązanie interfejsu użytkownika dla dokumentów i ramki.

`CDocTemplate` przechowuje liczbę dokumentów bez nazwy.

## <a name="cdocument"></a>CDocument

A `CDocument` jest własnością `CDocTemplate`.

Dokumenty mają listę aktualnie otwartych widoki (pochodną `CView`), wyświetlania dokumentu ( `CPtrList`).

Dokumenty nie utworzenia/zniszczenia widoków, ale są one dołączone do siebie nawzajem, po ich utworzeniu. Po zamknięciu dokumentu (oznacza to, za pomocą pliku/Close), wszystkie widoki dołączone zostanie zamknięte. Po zamknięciu ostatniego widoku do dokumentu (to znaczy, okno/Close) dokument zostanie zamknięty.

`CDocument::AddView`, `RemoveView` Interfejs jest używany do przechowywania listy widoku. `CDocument` jest zaprzyjaźniona z `CView` , dlatego możemy ustawić `CView::m_pDocument` wskaźnik Wstecz.

## <a name="cframewnd"></a>CFrameWnd

A `CFrameWnd` (ramki) odgrywa tę samą rolę jak 1.0 z MFC, ale teraz `CFrameWnd` klasy jest przeznaczony do użycia w wielu przypadkach bez dziedziczenia nowej klasy. Klasy pochodne `CMDIFrameWnd` i `CMDIChildWnd` są także rozszerzone, dlatego wiele standardowych poleceń są już zaimplementowane.

`CFrameWnd` Jest odpowiedzialny za tworzenie okien w obszarze klienta ramki. Zazwyczaj jest jedno okno główne uzupełnianie obszarów klienta ramki.

Okno ramek MDI obszaru klienta jest wypełniony formantu MDICLIENT, co z kolei jest nadrzędne względem wszystkich okien ramowych elementu podrzędnego MDI. Okno ramek SDI lub ramki okna elementu podrzędnego MDI obszaru klienta jest zwykle wypełniony `CView`-pochodzi obiekt okna. W przypadku właściwości `CSplitterWnd`, obszaru klienckiego widok jest wypełniany `CSplitterWnd` obiekt okna i `CView`— obiekty pochodne okna (po jednym dla każdej dzielone okienko) są tworzone jako okien podrzędnych `CSplitterWnd`.

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

