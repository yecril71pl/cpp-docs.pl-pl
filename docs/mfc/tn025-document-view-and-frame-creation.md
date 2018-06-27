---
title: 'Tn025: tworzenie Dokumentów, wyświetlać i ramek | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.creation
dev_langs:
- C++
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97db14dcb8c0b8b5b71823cf39d6bf36f0d19f25
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956697"
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025: tworzenie dokumentów, widoków i ramek
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga opisano problemy tworzenia i własność WinApps, DocTemplates, dokumentów, ramek i widoków.  
  
## <a name="winapp"></a>Aplikacji systemu Windows  
 Istnieje `CWinApp` obiektu w systemie.  
  
 Jest statycznie utworzone i zainicjowane przez implementację wewnętrznej struktury `WinMain`. Musi pochodzić od `CWinApp` wykonywania żadnych czynności przydatne (wyjątek: biblioteki DLL rozszerzeń MFC nie powinny mieć `CWinApp` wystąpienia — służą do inicjowania `DllMain` zamiast).  
  
 Co `CWinApp` listę szablonów dokumentów jest właścicielem obiektu ( `CPtrList`). Istnieje co najmniej jeden szablon dokumentu na aplikację. DocTemplates zazwyczaj są ładowane z pliku zasobów (to znaczy tablicy ciągów) w `CWinApp::InitInstance`.  
  
```  
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```  
  
 Co `CWinApp` wszystkie okna ramowe w aplikacji jest właścicielem obiektu. W oknie ramki głównej aplikacji powinny być przechowywane w `CWinApp::m_pMainWnd`; zwykle ustawić *m_pMainWnd* w `InitInstance` wykonania, jeśli nie ma umożliwić kreatorami AppWizard zrobił dla Ciebie. Dla interfejsu pojedynczego dokumentu (SDI) to jedna `CFrameWnd` służy jako okno ramowe aplikacji głównej, a także tylko ramkę okna dokumentu. W przypadku interfejsu wielu dokumentów (MDI) jest ramki MDI (klasa `CMDIFrameWnd`) służy jako okno ramowe aplikacji głównej, który zawiera wszystkie podrzędne `CFrameWnd`s. Każde okno podrzędne jest klasą `CMDIChildWnd` (pochodną `CFrameWnd`) i służy jako jeden z potencjalnie wiele okien ramowych dokumentu.  
  
## <a name="doctemplates"></a>DocTemplates  
 `CDocTemplate` Jest twórcę i Menedżera dokumentów. Dokumenty, które tworzy jest właścicielem. Jeśli aplikacja używa podejście oparte na zasobach opisane poniżej, nie trzeba będzie dziedziczyć `CDocTemplate`.  
  
 Dla aplikacji SDI klasy `CSingleDocTemplate` przechowuje informacje o jednym otwartego dokumentu. Dla aplikacji MDI klasy `CMultiDocTemplate` przechowuje listę ( `CPtrList`) z aktualnie otwarte dokumenty utworzone na podstawie tego szablonu. `CDocTemplate::AddDocument` i `CDocTemplate::RemoveDocument` zapewnienia wirtualny element członkowski funkcji dodawania i usuwania dokumentu z szablonu. `CDocTemplate` jest zaprzyjaźniona z `CDocument` , firma Microsoft można ustawić chronionej `CDocument::m_pDocTemplate` wskaźnik Wstecz, aby wskazywały szablonu dokumentu, której go utworzono.  
  
 `CWinApp` Domyślnie obsługuje `OnFileOpen` wdrożenia, który z kolei wysyła kwerendy do wszystkich szablonów dokumentów. Implementacja obejmuje wyszukiwanie już otwarte dokumenty i podejmowania decyzji o jakiego formatu Otwórz nowe dokumenty programu.  
  
 `CDocTemplate` zarządza powiązania interfejsu użytkownika dla dokumentów i ramki.  
  
 `CDocTemplate` Zlicza liczby dokumentów bez nazwy.  
  
## <a name="cdocument"></a>CDocument  
 A `CDocument` jest własnością `CDocTemplate`.  
  
 Dokumenty mają listę aktualnie otwartych widoków (pochodną `CView`) wyświetlany dokumentu ( `CPtrList`).  
  
 Dokumenty nie utworzenia/zniszczenia widoków, ale są one dołączone do siebie, po ich utworzeniu. Po zamknięciu dokumentu (to znaczy do pliku/Zamknij), wszystkie widoki dołączone zostanie zamknięte. Po zamknięciu ostatni widok w dokumencie (to znaczy, zamknij okno /) dokument zostanie zamknięty.  
  
 `CDocument::AddView`, `RemoveView` Interfejs jest używany w celu zachowania widoku listy. `CDocument` jest zaprzyjaźniona z `CView` , firma Microsoft można ustawić `CView::m_pDocument` wskaźnik Wstecz.  
  
## <a name="cframewnd"></a>CFrameWnd  
 A `CFrameWnd` (ramki) pełni tę samą rolę, tak jak MFC 1.0, ale teraz `CFrameWnd` klasy jest przeznaczona do użycia w wielu przypadkach bez wyprowadzanie nową klasę. Klasy pochodne `CMDIFrameWnd` i `CMDIChildWnd` również rozszerzono tak wiele standardowych poleceń są już wdrożone.  
  
 `CFrameWnd` Odpowiedzialną za tworzenie systemu windows w obszarze klienckim ramki. Zazwyczaj jest jedno okno główne uzupełnianie obszarów klienta ramki.  
  
 Okna ramowe MDI obszaru klienckiego jest wypełniony kontroli MDICLIENT, który z kolei jest nadrzędny wszystkich podrzędnych MDI okien ramowych. Okna ramowe SDI lub okno ramowe potomne MDI obszaru klienckiego jest zwykle wypełniony `CView`-pochodzi z obiektu okna. W przypadku programu `CSplitterWnd`, obszaru klienckiego widoku jest wypełniony `CSplitterWnd` obiekt window i `CView`-obiekty pochodne okna (po jednym w każdym okienku podziału) są tworzone jako okien podrzędnych z `CSplitterWnd`.  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

