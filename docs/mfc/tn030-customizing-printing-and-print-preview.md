---
title: 'TN030: dostosowywanie drukowania i podglądu wydruku'
ms.date: 06/28/2018
f1_keywords:
- vc.print
helpviewer_keywords:
- TN030
- customizing printing and print preview
- printing [MFC], views
- printing views [MFC]
- print preview [MFC], customizing
ms.assetid: 32744697-c91c-41b6-9a12-b8ec01e0d438
ms.openlocfilehash: 09938c5cec2812998d5e76e15154754ad3ac3e0b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667912"
---
# <a name="tn030-customizing-printing-and-print-preview"></a>TN030: dostosowywanie drukowania i podglądu wydruku

> [!NOTE]
> Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisuje proces dostosowywanie drukowania i podglądu wydruku oraz celów procedury wywołanie zwrotne używane w `CView` i procedury wywołania zwrotnego, jak i funkcje elementów członkowskich `CPreviewView`.

## <a name="the-problem"></a>Ten Problem

MFC udostępnia kompletne rozwiązanie dla większości drukowania i podglądu wydruku potrzebuje. W większości przypadków niewielkiej ilości kodu dodatkowe jest musi mieć możliwość drukowania i podglądu widoku. Jednak istnieją sposobów na optymalizację drukowania, która wymaga znaczących nakładów pracy przez dewelopera, a niektóre aplikacje, które należy dodać elementy interfejsu użytkownika do trybu podglądu wydruku.

## <a name="efficient-printing"></a>Wydajne drukowania

Po wydrukowaniu aplikację MFC przy użyciu standardowych metod Windows określa, że wszystkie wywołania metaplik w pamięci danych wyjściowych interfejsu urządzenia graficznego (GDI). Gdy `EndPage` jest wywoływana, Windows odgrywa metaplik jeden raz dla każdej fizycznej poza pasmem drukarki wymaga, aby drukować po jednej stronie. Podczas tego renderowania GDI często wykonuje zapytania przerwać procedury, aby określić, jeśli powinno być kontynuowane. Zazwyczaj procedury przerwania umożliwia wiadomości, które mają być przetwarzane, dzięki czemu użytkownik może przerwać zadanie drukowania, za pomocą okna dialogowego drukowania.

Niestety to może spowolnić proces drukowania. Jeśli drukowanie w aplikacji musi znajdować się szybciej, niż można osiągnąć przy użyciu standardowych technik, należy zaimplementować ręcznego podziału na przedziały.

## <a name="print-banding"></a>Drukuj pasma

Aby ręcznie pasmo, należy ponownie zaimplementować drukowania pętli taki sposób, że `OnPrint` jest wywoływana wiele razy na strony (raz na poza pasmem). Pętla wydruku jest zaimplementowana w `OnFilePrint` funkcji w viewprnt.cpp. W swojej `CView`-klasy, przeciążenie tej funkcji, aby wpisu mapy wiadomości do obsługi polecenia drukowania, wywołuje funkcję drukowania. Kopiuj `OnFilePrint` procedury i zmiana drukowania pętli do zaimplementowania pasma. Prawdopodobnie będziesz również mają być przekazane przedziały prostokąta do funkcji drukowania, dzięki czemu można zoptymalizować rysowania oparte na części strony, drukowanego.

Po drugie, często musisz wywołać `QueryAbort` podczas rysowania pasmo. W przeciwnym razie nie ma zostać wywołana procedura przerwać, a użytkownik będzie mógł anulować zadanie drukowania.

## <a name="print-preview-electronic-paper-with-user-interface"></a>Podgląd wydruku: Dokumentów elektronicznych przy użyciu interfejsu użytkownika

W zasadzie drukowania (wersja zapoznawcza), spróbuje włączyć wyświetlanie w emulację drukarki. Domyślnie obszaru klienckiego głównego okna służy do wyświetlania jednego lub dwóch stron w pełni w ramach okna. Użytkownik będzie mógł powiększać obszar strony, aby zobaczyć, jak to bardziej szczegółowo. Z dodatkową pomoc użytkownik może nawet mieć możliwość edytowania dokumentu w trybie podglądu.

## <a name="customizing-print-preview"></a>Dostosowywanie podglądu wydruku

Ta uwaga dotyczy tylko jeden z aspektów modyfikowanie podglądu wydruku: dodanie interfejsu użytkownika w trybie podglądu. Możliwe są inne modyfikacje, ale zmiany te są poza zakresem tej dyskusji.

## <a name="to-add-ui-to-the-preview-mode"></a>Aby dodać interfejs użytkownika do trybu podglądu

1. Wyprowadzić klasę z widoku `CPreviewView`.

2. Dodaj programy obsługi poleceń dla elementów interfejsu użytkownika, której wymagasz.

3. Jeśli dodajesz aspekty visual do wyświetlenia, zastępują `OnDraw` i wykonywać na rysunku po wywołaniu `CPreviewView::OnDraw`.

## <a name="onfileprintpreview"></a>OnFilePrintPreview

To jest program obsługi poleceń podglądu wydruku. Jego domyślna implementacja jest:

```cpp
void CView::OnFilePrintPreview()
{
    // In derived classes, implement special window handling here
    // Be sure to Unhook Frame Window close if hooked.

    // must not create this on the frame. Must outlive this function
    CPrintPreviewState* pState = new CPrintPreviewState;

    if (!DoPrintPreview(AFX_IDD_PREVIEW_TOOLBAR, this,
        RUNTIME_CLASS(CPreviewView), pState))
    {
        // In derived classes, reverse special window handling
        // here for Preview failure case

        TRACE0("Error: DoPrintPreview failed");
        AfxMessageBox(AFX_IDP_COMMAND_FAILURE);
        delete pState;  // preview failed to initialize, delete State now
    }
}
```

`DoPrintPreview` Spowoduje to ukrycie okienka głównego aplikacji. Paski sterowania, takie jak pasek stanu mogą być zachowywane przez, określając je w stanu wydajności ->*dwStates* elementu członkowskiego (jest to maski bitowej i bitów dla poszczególnych kontrolek paski zdefiniowano AFX_CONTROLBAR_MASK (AFX_IDW_MYBAR)). Stanu wydajności okna ->*nIDMainPane* jest oknem, które będą automatycznie ukryte i reshown. `DoPrintPreview` Spowoduje to utworzenie paska przycisków dla standardowego interfejsu użytkownika (wersja zapoznawcza). W razie specjalnych okna obsługi jest taki, aby ukryć lub pokazać inne okna, które powinny być wykonane przed `DoPrintPreview` jest wywoływana.

Domyślnie po zakończeniu podglądu wydruku, zwraca paski sterowania do ich oryginalnej stanów i okienka głównego, aby widoczne. Jeśli potrzebne jest specjalnej obsługi, należy to zrobić w zastąpieniu obiektu `EndPrintPreview`. Jeśli `DoPrintPreview` zakończy się niepowodzeniem, a także podać specjalnej obsługi.

DoPrintPreview jest wywoływana z:

- Identyfikator zasobu szablonu okna dialogowego dla paska narzędzi w wersji zapoznawczej.

- Wskaźnik do widoku na potrzeby przeprowadzenia drukowanie podglądu wydruku.

- Klasa czasu wykonywania klasa widoku (wersja zapoznawcza). Będzie można dynamicznie utworzyć w DoPrintPreview.

- Wskaźnik CPrintPreviewState. Uwaga musi struktury CPrintPreviewState (lub pochodny struktury, jeśli aplikacja potrzebuje więcej stanu zachowanego) *nie* można utworzyć w ramce. DoPrintPreview jest niemodalne, a ta struktura musi być odporny, dopóki EndPrintPreview jest wywoływana.

  > [!NOTE]
  > Jeśli potrzebne jest oddzielne widoku lub widok klasy obsługę drukowania, wskaźnik do tego obiektu powinien zostać przekazany jako drugi parametr.

## <a name="endprintpreview"></a>EndPrintPreview

Jest to, aby zakończyć tryb podglądu wydruku. Często jest to pożądane, aby przejść do strony w dokumencie, który został ostatnio wyświetlane w podglądzie wydruku. `EndPrintPreview` Umożliwia to aplikacji masz szansę, aby to zrobić. -> PInfo*m_nCurPage* elementu członkowskiego jest strona, która została ostatnio wyświetlane (po lewej stronie, jeśli były wyświetlane dwie strony) i wskaźnik jest wskazówkę, gdzie na stronie użytkownika został chcesz się dowiedzieć. Ponieważ struktura widoku aplikacji jest nieznany w ramach, należy podać kod, aby przejść do wybranego miejsca.

Należy wykonać większość akcji przed wywołaniem `CView::EndPrintPreview`. To wywołanie odwraca skutki `DoPrintPreview` i usuwa pView podstawowego kontrolera domeny i pInfo.

```cpp
// Any further cleanup should be done here.
CView::EndPrintPreview(pDC, pInfo, point, pView);
```

## <a name="cwinapponfileprintsetup"></a>CWinApp::OnFilePrintSetup

Musi to być mapowane dla elementu menu Ustawienia wydruku. W większości przypadków nie jest konieczne do przesłonięcia implementację.

## <a name="page-nomenclature"></a>Nomenklatura strony

Innym problemem jest numerowania i zamówienia. W przypadku aplikacji typu prostego edytora tekstów jest prosty problem. Większość systemów podglądu wydruku przyjęto założenie, że każdej strony wydruku odpowiada jedną stronę w dokumencie.

Podczas próby stanowią rozwiązanie uogólniony, istnieje kilka kwestii, które należy wziąć pod uwagę. Wyobraź sobie CAD system. Użytkownik ma rysunku, który obejmuje kilka arkuszy rozmiar E. Rozmiar E (lub mniejsze) ploterów, numerowania mogłoby wyglądać tak jak w przypadku prostych. Jednak na drukarka laserowa, drukowanie 16 stron A rozmiar na arkusz, co to Podgląd wydruku należy wziąć pod uwagę "page"

Jak Stany akapit wprowadzający, Podgląd wydruku działa jak do drukarki. W związku z tym użytkownik będzie widział co przybyły spoza określonej drukarki, która jest zaznaczone. Jest widok, aby ustalić, jakie wydruku na każdej stronie.

Ciąg opisu strony w `CPrintInfo` struktura zapewnia sposób wyświetlania numer strony do użytkownika, jeśli może być reprezentowany jako cyfra na stronie (tak jak "Strona 1" lub "strony 1-2"). Ten ciąg jest używany przez domyślną implementację elementu `CPreviewView::OnDisplayPageNumber`. W razie potrzeby innego ekranu jeden mogą zastąpić tę wirtualnego funkcję, aby zapewnić, na przykład "Arkusz1, sekcje A, B".

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
