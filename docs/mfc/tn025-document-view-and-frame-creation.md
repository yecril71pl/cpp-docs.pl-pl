---
title: 'TN025: tworzenie dokumentów, widoków i ramek'
ms.date: 11/04/2016
f1_keywords:
- vc.creation
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
ms.openlocfilehash: 2fdabdcb1a87d4a5661348588d49303290c966ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370368"
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025: tworzenie dokumentów, widoków i ramek

> [!NOTE]
> Następująca uwaga techniczna nie została zaktualizowana, ponieważ została po raz pierwszy uwzględniona w dokumentacji online. W rezultacie niektóre procedury i tematy mogą być nieaktualne lub nieprawidłowe. Aby uzyskać najnowsze informacje, zaleca się wyszukicie tematu interesującego w indeksie dokumentacji online.

W tej notatce opisano problemy z tworzeniem i własnością dla aplikacji WinApps, DocTemplates, Documents, Frames i Views.This note describes the creation and ownership issues for WinApps, DocTemplates, Documents, Frames and Views.

## <a name="winapp"></a>WinApp (właśc.

W systemie `CWinApp` znajduje się jeden obiekt.

Jest statycznie skonstruowany i zainicjowany przez wewnętrzne `WinMain`wdrożenie ram . Musisz wyprowadzić `CWinApp` z zrobić coś przydatne (wyjątek: DLL rozszerzenia `CWinApp` MFC nie powinny `DllMain` mieć wystąpienie — inicjowanie odbywa się zamiast).

Jeden `CWinApp` obiekt jest właścicielem listy szablonów `CPtrList`dokumentów (a ). Istnieje jeden lub więcej szablonów dokumentów dla aplikacji. DocTemplates są zwykle ładowane z pliku zasobu `CWinApp::InitInstance`(czyli tablicy ciągów) w pliku .

```
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```

Jeden `CWinApp` obiekt jest właścicielem wszystkich okien ramki w aplikacji. Okno ramki głównej dla aplikacji `CWinApp::m_pMainWnd`powinno być przechowywane w ; zwykle ustawiasz *m_pMainWnd* w `InitInstance` implementacji, jeśli nie pozwoliłeś AppWizard zrobić to za Ciebie. W przypadku interfejsu pojedynczego dokumentu (SDI) jest to okno, `CFrameWnd` które służy jako główne okno ramki aplikacji, a także jedyne okno ramki dokumentu. Dla wielu interfejsów dokumentu (MDI) jest to `CMDIFrameWnd`RAMKA MDI (klasa), który służy `CFrameWnd`jako okno ramki aplikacji głównej, która zawiera wszystkie elementy podrzędne s. Każde okno podrzędne `CMDIChildWnd` jest klasy `CFrameWnd`(pochodzi od ) i służy jako jeden z potencjalnie wielu okien ramki dokumentu.

## <a name="doctemplates"></a>DocTemplates

Jest `CDocTemplate` twórcą i menedżerem dokumentów. Jest właścicielem dokumentów, które tworzy. Jeśli aplikacja korzysta z podejścia opartego na zasobach opisanego poniżej, nie będzie musiała pochodzić z `CDocTemplate`programu .

Dla aplikacji SDI klasa `CSingleDocTemplate` śledzi jeden otwarty dokument. Dla aplikacji MDI klasa `CMultiDocTemplate` przechowuje listę `CPtrList`(a) wszystkich aktualnie otwartych dokumentów utworzonych na podstawie tego szablonu. `CDocTemplate::AddDocument`i `CDocTemplate::RemoveDocument` udostępnij funkcje wirtualnego elementu członkowskiego do dodawania lub usuwania dokumentu z szablonu. `CDocTemplate`jest `CDocument` przyjacielem, dzięki czemu możemy `CDocument::m_pDocTemplate` ustawić chroniony wskaźnik wstecz, aby wskazać z powrotem do szablonu dokumentu, który utworzył dokument.

`CWinApp`obsługuje domyślną `OnFileOpen` implementację, która z kolei będzie wysyłać zapytania do wszystkich szablonów doc. Implementacja obejmuje poszukiwanie już otwartych dokumentów i podejmowanie decyzji, w jakim formacie otworzyć nowe dokumenty.

`CDocTemplate`zarządza powiązaniem interfejsu użytkownika dla dokumentów i ramek.

`CDocTemplate`przechowuje liczbę nienazwanych dokumentów.

## <a name="cdocument"></a>Cdocument

A `CDocument` jest własnością `CDocTemplate`.

Dokumenty mają listę aktualnie otwartych widoków `CView`(pochodzących z ), `CPtrList`które wyświetlają dokument (a ).

Dokumenty nie tworzą/nie niszczą widoków, ale są dołączone do siebie po ich utworzeniu. Gdy dokument zostanie zamknięty (czyli za pośrednictwem pliku/zamknięcia), wszystkie dołączone widoki zostaną zamknięte. Po zamknięciu ostatniego widoku dokumentu (czyli Okno/Zamknij) dokument zostanie zamknięty.

Interfejs `CDocument::AddView` `RemoveView` , służy do obsługi listy widoków. `CDocument`jest przyjacielem, `CView` dzięki czemu `CView::m_pDocument` możemy ustawić wskaźnik z tyłu.

## <a name="cframewnd"></a>CFrameWnd

A `CFrameWnd` (znany również jako ramka) odgrywa taką samą rolę jak w `CFrameWnd` MFC 1.0, ale teraz klasa jest przeznaczony do użycia w wielu przypadkach bez wyprowadzania nowej klasy. Klasy `CMDIFrameWnd` pochodne `CMDIChildWnd` i są również rozszerzone tak wiele standardowych poleceń są już zaimplementowane.

Jest `CFrameWnd` odpowiedzialny za tworzenie okien w obszarze klienta ramki. Zwykle jest jedno główne okno wypełniające obszar klienta ramy.

W przypadku okna RAMKA MDI obszar klienta jest wypełniony kontrolką MDICLIENT, która z kolei jest elementem nadrzędnym wszystkich okien ramek MDI-Child. W przypadku okna SDI-Frame lub okna ramki MDI-Child obszar `CView`klienta jest zwykle wypełniony obiektem okna pochodnym. W przypadku `CSplitterWnd`obszaru klienta widoku jest wypełniona `CSplitterWnd` obiektem okna, `CView`a obiekty okna pochodnego (po jednym na podzielone `CSplitterWnd`okienko) są tworzone jako okna podrzędne .

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
