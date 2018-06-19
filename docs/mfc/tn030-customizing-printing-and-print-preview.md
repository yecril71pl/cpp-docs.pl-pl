---
title: 'TN030: Dostosowywanie drukowania i podglądu wydruku | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.print
dev_langs:
- C++
helpviewer_keywords:
- TN030
- customizing printing and print preview
- printing [MFC], views
- printing views [MFC]
- print preview [MFC], customizing
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 342edd56ee279de0b854c8e8ceb177b797a03f3b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384614"
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030: dostosowywanie drukowania i podglądu wydruku
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga opisuje proces dostosowywanie drukowania i podglądu wydruku oraz na potrzeby procedury wywołania zwrotnego używane w `CView` oraz procedury wywołania zwrotnego i funkcje Członkowskie **CPreviewView**.  
  
## <a name="the-problem"></a>Problem  
 MFC zapewnia kompleksowe rozwiązanie dla większości drukowania i podglądu wydruku musi. W większości przypadków małego dodatkowy kod jest musi mieć możliwość drukowania i podglądu widoku. Jednak można zoptymalizować drukowanie sposobów wymagające znacznego wysiłku przez dewelopera, a niektóre aplikacje należy dodać elementy interfejsu użytkownika do trybu podglądu wydruku.  
  
## <a name="efficient-printing"></a>Efektywne drukowania  
 Gdy aplikacji MFC drukuje przy użyciu standardowych metod, Windows określa, że wszystkie wywołania metaplik w pamięci danych wyjściowych graficzny interfejs urządzenia (GDI). Gdy `EndPage` jest wywoływana, odgrywa systemu Windows metafile raz dla każdej grupy fizycznych, której drukarki wymaga, aby wydrukować jedną stronę. Podczas tego renderowania GDI często wysyła zapytanie do przerwania procedurę, aby określić, czy należy kontynuować. Zwykle procedura przerwania pozwala komunikaty do przetwarzania, dzięki czemu użytkownik może przerwać zadanie drukowania przy użyciu okna dialogowego drukowania.  
  
 Niestety może to spowodować proces drukowania. Jeśli drukowanie w aplikacji musi być szybciej, niż można osiągnąć za pomocą standardowych technika, musisz zaimplementować ręczne pasma.  
  
## <a name="print-banding"></a>Drukowanie pasma  
 Aby ręcznie pasmo, musisz re zaimplementować wydruku pętli tak, aby `OnPrint` jest wywołana wiele razy na stronie (raz na poza pasmem). Pętla wydruku jest zaimplementowana w **OnFilePrint** w viewprnt.cpp funkcji. W Twojej `CView`-klasy, przeciążenia tej funkcji, dzięki czemu wpisu mapy komunikatów dla obsługi drukowania polecenia wywołania funkcji drukowania. Kopiuj **OnFilePrint** procedury i zmień wydruku pętli do zaimplementowania pasma. Prawdopodobnie będziesz chce również przekazać przedziały prostokąta do funkcji drukowania, aby zoptymalizować rysunku oparte na części drukowanej strony.  
  
 Po drugie, często należy wywołać `QueryAbort` podczas rysowania grupy. W przeciwnym razie nie będzie uzyskać nazwę procedury przerwania i użytkownik będzie mógł anulować zadanie drukowania.  
  
## <a name="print-preview-electronic-paper-with-user-interface"></a>Podgląd wydruku: Papieru elektronicznych z interfejsem użytkownika  
 Podgląd wydruku w zasadzie próbuje wyświetlacz do emulacji drukarki. Domyślnie obszar klienta okna głównego służy do wyświetlania jednego lub dwóch stron w pełni w ramach okna. Użytkownik jest w stanie powiększyć obszar strony, aby wyświetlić więcej szczegółów. Z obsługą dodatkowych użytkownik może nawet można edytować dokument w wersji zapoznawczej.  
  
## <a name="customizing-print-preview"></a>Dostosowywanie podglądu wydruku  
 Ta uwaga dotyczy tylko jednego aspektu modyfikowanie podglądu wydruku: Dodawanie interfejsu użytkownika do trybu podglądu. Inne zmiany są możliwe, ale zmiany te są poza zakresem tej dyskusji.  
  
## <a name="to-add-ui-to-the-preview-mode"></a>Aby dodać interfejsu użytkownika do trybu podglądu  
  
1.  Klasa wyprowadzona z widoku **CPreviewView**.  
  
2.  Dodaj programy obsługi poleceń dla elementów interfejsu użytkownika, której wymagasz.  
  
3.  Jeśli dodajesz visual aspekty do wyświetlenia, Zastąp `OnDraw` i wykonywać na rysunku po wywołaniu **CPreviewView::OnDraw.**  
  
## <a name="onfileprintpreview"></a>OnFilePrintPreview  
 To jest programem obsługi podglądu wydruku. Jego domyślna implementacja jest:  
  
```  
void CView::OnFilePrintPreview()  
{ *// In derived classes,
    implement special window handling here *// Be sure to Unhook Frame Window close if hooked.  
 *// must not create this on the frame. Must outlive this function  
    CPrintPreviewState* pState = new CPrintPreviewState;  
 
    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR,
    this,  
    RUNTIME_CLASS(CPreviewView),
    pState))  
 { *// In derived classes,
    reverse special window handling *// here for Preview failure case  
 
    TRACE0("Error: DoPrintPreview failed");

    AfxMessageBox(AFX_IDP_COMMAND_FAILURE);

 delete pState;      // preview failed to initialize, *// delete State now  
 }  
}  
```  
  
 **DoPrintPreview** spowoduje ukrycie okienka głównego aplikacji. Paski sterowania, np. paska stanu mogą być przechowywane, określając je w stanu wydajności ->**dwStates** elementu członkowskiego (jest to maska bitowa i bitów dla poszczególnych kontrolek paski są definiowane przez **AFX_CONTROLBAR_MASK**(AFX_IDW_MYBAR)). Stanu okna wydajności ->**nIDMainPane** okna, które będą automatycznie ukryte i reshown. **DoPrintPreview** spowoduje to utworzenie paska przycisków dla standardowego interfejsu użytkownika podglądu. W razie potrzeby specjalne okno obsługi takie, aby pokazać lub ukryć innych oknach, które należy wykonać przed **DoPrintPreview** jest wywoływana.  
  
 Domyślnie po zakończeniu podglądu wydruku, zwraca paski sterowania do ich oryginalnej stanów i okienku głównym, aby widoczne. Jeśli specjalnej obsługi nie jest konieczne, należy to zrobić w zastępująca **EndPrintPreview.** Jeśli **DoPrintPreview** kończy się niepowodzeniem, a także podać specjalnej obsługi.  
  
 DoPrintPreview jest wywoływana z:  
  
-   Identyfikator zasobu szablonu okna dialogowego paska narzędzi podglądu.  
  
-   Wskaźnik do widoku do wykonywania drukowania podglądu wydruku.  
  
-   Klasa czasu wykonywania klasy podglądu widoku. Będzie można dynamicznie utworzyć w DoPrintPreview.  
  
-   Wskaźnik CPrintPreviewState. Należy pamiętać, że struktura CPrintPreviewState (lub pochodne struktury, jeśli aplikacja wymaga więcej stanu zachowanego) musi *nie* można utworzyć w ramce. DoPrintPreview jest niemodalne i musi być odporny tej struktury, dopóki EndPrintPreview jest wywoływana.  
  
    > [!NOTE]
    >  Jeśli wymagane jest osobny widok lub klasy widoku dla obsługę drukowania, wskaźnik do obiektu powinien zostać przekazany jako drugiego parametru.  
  
## <a name="endprintpreview"></a>EndPrintPreview  
 Jest to, aby zakończyć tryb podglądu wydruku. Często jest to pożądane, aby przejść do strony w dokumencie, który został ostatnio wyświetlane w podglądzie wydruku. **EndPrintPreview** ryzyko aplikacji, w tym celu. -> PInfo`m_nCurPage` element członkowski jest strona, która została ostatnio wyświetlane (po lewej stronie, jeśli były wyświetlane dwie strony), a wskaźnik jest wskazówkę, gdy na stronie użytkownik został zainteresowanych. Ponieważ struktura widoku aplikacji jest nieznany w ramach, musisz podać kod, aby przejść do wybranego punktu.  
  
 Należy wykonać większość akcji przed wywołaniem **CView::EndPrintPreview**. To wywołanie odwraca skutków **DoPrintPreview** i usuwa pView podstawowego kontrolera domeny i pInfo.  
  
```  
// Any further cleanup should be done here.  
CView::EndPrintPreview(pDC,
    pInfo,
    point,
    pView);
```  
  
## <a name="cwinapponfileprintsetup"></a>CWinApp::OnFilePrintSetup  
 To musi być zamapowany dla elementu menu Ustawienia wydruku. W większości przypadków nie jest konieczne do przesłonięcia implementację.  
  
## <a name="page-nomenclature"></a>Nomenklatura strony  
 Inny problem dotyczy numerowania i kolejność. Dla aplikacji typu prostego edytora tekstów jest to prosta problem. Większość systemów podglądu wydruku założono, że każdy wydrukowaną stroną odpowiada jedną stronę w dokumencie.  
  
 Podczas próby uogólniony rozwiązanie, istnieje kilka kwestii, które należy wziąć pod uwagę. Wyobraź sobie systemu CAD. Użytkownik ma rysunku, który obejmuje kilka arkuszy E rozmiar. Na rozmiar E (lub mniejsze, skalowania) miał, numerowania będzie tak jak w przypadku prostych. Jednak na drukarka laserowa, drukowanie 16 A rozmiar stron na arkuszu, co to Podgląd wydruku należy wziąć pod uwagę "page"  
  
 Jak Stany wprowadzające akapitu, Podgląd wydruku działa jak do drukarki. W związku z tym użytkownik będzie widział co przybyły poza określonym drukarki, która jest zaznaczona. Jest widok, aby ustalić, jakie wydruku na każdej stronie.  
  
 Ciąg opisu strony w `CPrintInfo` struktury umożliwia wyświetlanie numer strony do użytkownika, jeśli może być reprezentowany jako jeden numer na stronie (tak jak "Strona 1" lub "strony 1-2"). Ten ciąg jest używany przez domyślną implementację elementu **CPreviewView::OnDisplayPageNumber**. W razie potrzeby inną wyświetlaną jedną mogą zastępować tej funkcji wirtualnego, aby zapewnić, na przykład "Sheet1 —, A sekcje B".  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

