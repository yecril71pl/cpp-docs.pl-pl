---
title: 'TN040: MFC OLE w miejscu Zmienianie rozmiaru i powiększanie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.ole
dev_langs:
- C++
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf8b90aed96135967167c8048f775fc7530f85d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040: MFC/OLE — zmienianie rozmiaru i powiększanie w miejscu
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga będzie omawiać problemy odnoszące się do edycji w miejscu i jak serwer powinien wykonać poprawną powiększanie i zmiany rozmiaru w miejscu. Aktywacja w miejscu WYSIWYG koncepcja jest zajęta krok dalej w tym kontenery i serwery współpracować ze sobą, a w szczególności zinterpretować ze specyfikacją OLE w taki sam sposób.  
  
 Z powodu zamknięcia interakcji między kontenera i serwera obsługującego Aktywacja w miejscu istnieje wiele oczekiwań od użytkownika końcowego, który należy utrzymywać:  
  
-   Wyświetlanie prezentacji (metaplik na środku `COleServerItem::OnDraw` zastąpienia) powinien wyglądać dokładnie takie same jak podczas rysowania do edycji (z wyjątkiem tego, że narzędzia do edycji nie są widoczne).  
  
-   Gdy powiększa kontenera, okno serwer powinien zbyt!  
  
-   Obiekty do edycji przy użyciu tego samego metryki powinien być wyświetlany kontenera i serwera. Oznacza to, za pomocą tryb mapowania na podstawie liczby *logicznej* pikseli na cal — nie fizycznych pikseli na cal, podczas renderowania na urządzenia.  
  
> [!NOTE]
>  Ponieważ aktywacja w miejscu dotyczy tylko elementów, które są osadzone (niepołączone), powiększając ma zastosowanie tylko do obiektów osadzonych. Zobaczysz interfejsów API w obu `COleServerDoc` i `COleServerItem` służące do powiększania. Przyczyna tego dichotomy są tylko funkcje, które są prawidłowe dla połączonych i osadzonych elementów w `COleServerItem` (dzięki temu można mieć wspólne implementacji) i funkcje, które są prawidłowe tylko dla osadzonych obiektów znajdują się w `COleServerDoc` klasy (z perspektywy serwera jest `document` którego jest osadzony).  
  
 Większość obciążeń jest umieszczona na implementujący serwera, serwer musi mieć świadomość współczynnika powiększenia kontenera i zmodyfikować jego edycji interfejs zależnie od potrzeb. Jednak serwer ustalić sposób korzystających z kontenera współczynnika powiększenia  
  
## <a name="mfc-support-for-zooming"></a>Obsługa MFC dla powiększania  
 Można określić bieżącego współczynnika powiększenia przez wywołanie metody `COleServerDoc::GetZoomFactor`. To wywołanie, gdy dokument nie jest aktywny w miejscu zawsze spowoduje współczynnika powiększenia 100% (lub stosunek 1:1). Wywoływanie jej, gdy aktywny w miejscu, mogą zwracać inną niż 100%.  
  
 Przykład poprawnie powiększanie Zobacz przykład MFC OLE [HIERSVR](../visual-cpp-samples.md). Powiększanie HIERSVR jest złożona przez fakt, że wyświetla tekst i tekst, ogólnie rzecz biorąc, nie działa w sposób liniowy (wskazówek, Konwencji typograficznych, projekt szerokości i wysokości wszystkich skomplikować sprawy). Nadal, HIERSVR jest uzasadnione odwołanie wykonywania powiększanie prawidłowo, i dlatego jest samouczek MFC [BAZGROŁY](../visual-cpp-samples.md) (krok 7).  
  
 `COleServerDoc::GetZoomFactor` Określa współczynnika powiększenia na podstawie liczby różnych dostępnych metryk z kontenera lub ze stosowania sieci `COleServerItem` i `COleServerDoc` klasy. Krótko mówiąc bieżący współczynnika powiększenia jest określany przez następującej formuły:  
  
```  
Position Rectangle (PR) / Container Extent (CE)  
```  
  
 Pozycja prostokąta zależy kontenera. Jest zwracany do serwera podczas aktywacji w miejscu po `COleClientItem::OnGetItemPosition` nosi nazwę i jest aktualizowany, gdy kontener wywoła serwera `COleServerDoc::OnSetItemRects` (w wyniku wywołania `COleClientItem::SetItemRects`).  
  
 W zakresie kontenera jest nieco bardziej skomplikowane do obliczenia. Jeśli kontener została wywołana `COleServerItem::OnSetExtent` (w wyniku wywołania `COleClientItem::SetExtent`), ta wartość konwertowana na pikseli na podstawie liczby pikseli na cal logiczny jest w zakresie kontenera. Kontener nie została wywołana SetExtent (co jest zazwyczaj sytuacją), a następnie w zakresie kontenera jest rozmiar zwrócony z `COleServerItem::OnGetExtent`. Tak, jeśli kontener nie została wywołana SetExtent, platformę przyjęto założenie, że jeśli jak kontenera czy wywołano go o 100% fizycznych zakres (wartość zwracana z **COleServerItem::GetExtent**). Wyrażony w inny sposób ramach przyjęto założenie, że w kontenerze są wyświetlane 100% (nie więcej, nie mniejszą) elementu.  
  
 Należy pamiętać, że chociaż `COleServerItem::OnSetExtent` i `COleServerItem::OnGetExtent` mają podobne nazwy ich nie manipulowania tego samego atrybutu element. `OnSetExtent` jest wywoływana, aby umożliwić serwera wiedzieć, ile obiektu jest widoczny w kontenerze (niezależnie od współczynnika powiększenia) i `OnGetExtent` jest wywoływana przez kontener, aby określić rozmiar idealny obiektu.  
  
 Patrząc na każdy z interfejsów API związanego, możesz uzyskać jaśniejszy obraz:  
  
## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent  
 Ta funkcja powinna zwrócić "fizycznych rozmiar" w jednostkach HIMETRIC elementu. Najlepszym sposobem traktować "rozmiar fizyczną" jest definiować go jako rozmiar, który może pojawiać się po wydrukowaniu. Rozmiar zwracane w tym miejscu jest stałe dla zawartości określonego elementu, (podobne jak w przypadku metaplik, który jest stały dla danego elementu). Ten rozmiar nie zmienia się podczas powiększania jest stosowany do elementu. Zazwyczaj nie zmienia się podczas kontener zawiera element więcej lub mniej miejsca przez wywołanie metody `OnSetExtent`. Przykładem zmiany może być prosty edytor tekstowy nie możliwości "margines", który opakowany tekstu opartych na ostatni zakres wysyłane przez kontener. Jeśli serwer ulega zmianie, serwer prawdopodobnie należy ustawić OLEMISC_RECOMPOSEONRESIZE bitu w rejestrze systemu (zobacz dokumentacji zestawu SDK OLE, aby uzyskać więcej informacji na temat tej opcji).  
  
## <a name="coleserveritemonsetextent"></a>COleServerItem::OnSetExtent  
 Ta funkcja jest wywoływana, gdy kontener zawiera "bardziej lub mniej" obiektu. Większość kontenerów nie wywoła to wcale. Domyślna implementacja przechowuje ostatnią wartość otrzymanych w kontenerze "m_sizeExtent", który jest używany w `COleServerDoc::GetZoomFactor` podczas obliczania wartości zakresu kontenera opisane powyżej.  
  
## <a name="coleserverdoconsetitemrects"></a>COleServerDoc::OnSetItemRects  
 Ta funkcja jest wywoływana tylko wtedy, gdy dokument jest aktywny w miejscu. Jest ona wywoływana podczas aktualizacji kontenera położenie elementu lub wycinka stosowany do elementu. Pozycja prostokąta, jak wspomniano powyżej, zapewnia licznik Obliczanie współczynnika powiększenia. Serwer może zażądać zmiana położenie elementu przez wywołanie metody `COleServerDoc::RequestPositionChange`. Kontener może lub nie może odpowiedzieć na to żądanie przez wywołanie metody `OnSetItemRects` (w wyniku wywołania **COleServerItem::SetItemRects**).  
  
## <a name="coleserverdocondraw"></a>COleServerDoc::OnDraw  
 Ważne jest, aby należy pamiętać, że metaplik utworzony przez zastąpienie `COleServerItem::OnDraw` tworzy dokładnie tego samego metaplik, niezależnie od bieżącej współczynnika powiększenia. Kontener skalują metaplik zależnie od potrzeb. Jest to ważna różnica między widoku `OnDraw` elementu serwera i `OnDraw`. Po prostu tworzy uchwytów wyświetlanie, powiększanie, element *którą można powiększać* metaplik pozostawia do kontenera, aby wykonać odpowiednie powiększania.  
  
 Najlepszy sposób, aby upewnić się, że serwer działa prawidłowo, jest użycie implementacji `COleServerDoc::GetZoomFactor` Jeśli dokument jest aktywny w miejscu.  
  
## <a name="mfc-support-for-in-place-resizing"></a>Obsługa MFC do zmiany rozmiaru w miejscu  
 MFC pełni implementuje interfejs zmiany rozmiaru w miejscu, zgodnie z opisem w specyfikacji OLE 2. Interfejs użytkownika jest obsługiwany przez `COleResizeBar` klasy niestandardowy komunikat **WM_SIZECHILD**i specjalnej obsługi tego komunikatu w `COleIPFrameWnd`.  
  
 Można zaimplementować różnych Obsługa tego komunikatu, niż dostarczanych przez platformę. Zgodnie z powyższym opisem platformę pozostawia wyniki do kontenera zmiany rozmiaru w miejscu — serwer odpowiada na Zmiana współczynnika powiększenia. Jeśli kontener reaguje ustawiając zarówno zakres kontenera i pozycja prostokąta podczas przetwarzania jego `COleClientItem::OnChangeItemPosition` (wywołać wyniku wywołania `COleServerDoc::RequestPositionChange`), a następnie zmiany rozmiaru w miejscu spowoduje przedstawiający "bardziej lub mniej" elementu w edycji okno. Jeśli kontener reaguje tylko ustawienie pozycja prostokąta podczas przetwarzania `COleClientItem::OnChangeItemPosition`, zmieni współczynnika powiększenia i elementu zostaną wyświetlone "powiększony przychodzący lub wychodzący."  
  
 Serwer można kontrolować (w pewnym stopniu), co się dzieje podczas tej negocjacji. Arkusz kalkulacyjny, na przykład może zdecydować się na Pokaż więcej lub mniej komórek, gdy użytkownik zmienia rozmiar okna podczas edycji elementu w miejscu. Word-processor może zdecydować się na zmiany "marginesach strony", są takie same jak okna i zawijany do nowego marginesu. Serwery wdrożyć przez zmianę w zakresie fizycznych (rozmiar zwrócony z `COleServerItem::OnGetExtent`) po zakończeniu zmiany rozmiaru. Spowoduje to pozycja prostokąta jak również w zakresie kontenera, aby zmienić tę samą wartość, co w tym samym współczynnika powiększenia, ale większy lub mniejszy obszar wyświetlania. Ponadto, bardziej lub mniej dokumentu będą widoczne w metaplik generowane przez `OnDraw`. W takim przypadku samego dokumentu jest zmiana, gdy użytkownik zmienia rozmiar elementu, a nie tylko obszaru wyświetlania.  
  
 Można zaimplementować niestandardowych zmiana rozmiaru i nadal korzystać z interfejsu użytkownika udostępniane przez `COleResizeBar` przez zastąpienie **WM_SIZECHILD** wiadomości w sieci `COleIPFrameWnd` klasy. Aby uzyskać więcej informacji na temat **WM_SIZECHILD**, zobacz [24 Uwaga techniczna](../mfc/tn024-mfc-defined-messages-and-resources.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

