---
title: Formanty ActiveX w Internecie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [MFC], creating
- ActiveX controls [MFC], Internet
- downloading data with ActiveX controls
- OLE controls [MFC], upgrading to ActiveX
- Internet applications [MFC], ActiveX controls
- networks [MFC], downloading with ActiveX controls
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02a4c2e8d9da553ffe14c8d9d061d11d7357c19c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931980"
---
# <a name="activex-controls-on-the-internet"></a>Kontrolki ActiveX w Internecie
Formanty ActiveX są zaktualizowaną wersję specyfikacji formantu OLE. Formanty są podstawowej architektury do tworzenia składników programowalny oprogramowania, których można użyć w wielu różnych kontenerów, w tym przeglądarek sieci Web obsługującej COM w Internecie. Formantu ActiveX mogą być formantu Internet i można dodać jego działanie do aktywnego dokumentu lub być częścią strony sieci Web. Formanty na stronie sieci Web może komunikować się ze sobą za pomocą skryptów.  
  
 Formanty ActiveX nie są ograniczone do Internetu. Kontrolki ActiveX można również w dowolnym kontenerze tak długo, jak kontrolka obsługuje interfejsy wymagane przez tego kontenera.  
  
 **Kontrolki ActiveX ma kilka zalet, w tym:**  
  
-   Interfejsy mniej wymagane niż poprzednie formantów OLE.  
  
-   Możliwość można bez okien i zawsze aktywny w miejscu.  
  
 **Aby mogła być formantu ActiveX, formantu musi:**  
  
-   Obsługa `IUnknown` interfejsu.  
  
-   Być obiektem COM.  
  
-   Eksportuj **DLLRegisterServer** i **DLLUnRegisterServer**.  
  
-   Obsługuje dodatkowe interfejsy, w razie potrzeby dla funkcji.  
  
## <a name="making-your-existing-controls-internet-friendly"></a>Tworzenie z istniejących formantów Internet przyjaznego  
 Projektowanie formant, który będzie działać poprawnie w środowisku sieci Internet wymaga zaplanowania małą szybkością w Internecie. Korzystając z istniejących formantów; Istnieją jednak czynności, które należy podjąć, aby zmniejszyć rozmiar kodu i aby asynchronicznie pobrać właściwości formantu.  
  
 Aby zwiększyć wydajność formantów, wykonaj te wskazówki dotyczące zagadnienia dotyczące wydajności:  
  
-   Wdrożenie metod opisanych w artykule [formantów ActiveX: Optymalizacja](../mfc/mfc-activex-controls-optimization.md).  
  
-   Należy wziąć pod uwagę, jak formantu zostanie uruchomiony.  
  
-   Była asynchroniczna; nie utrzymanie innych programów.  
  
-   Pobieranie danych w małych bloków.  
  
     Podczas pobierania dużych strumieni, takie jak map bitowych lub danych wideo, dostęp do danych formantu asynchronicznie we współpracy z kontenera. Pobieranie danych w sposób przyrostowy lub progresywnego pracy wspólnie z innymi formantami, które mogą również pobieranie danych. Kod może również być asynchronicznie pobierania.  
  
-   Pobierz kod i właściwości w tle.  
  
-   Stają się interfejs użytkownika active tak szybko jak to możliwe.  
  
-   Należy rozważyć sposób trwałego dane są przechowywane, zarówno właściwości i dużej ilości danych obiektów blob (np. danych image lub wideo mapy bitowej).  
  
     Formanty z znacznej ilości danych trwałych, takie jak duża map bitowych lub plików AVI wymagają dokładne uwagi do pobierania — metoda. Dokument lub strony można tak szybko, jak to możliwe stają się widoczne i Zezwalaj użytkownikom na interakcję z strony podczas kontroli pobierania danych w tle.  
  
-   Zapis efektywne procedury, aby zachować rozmiar kodu i czasu wykonywania w dół.  
  
     Małych kontrolek przycisków i etykiet, zawierających tylko kilka bajtów trwałych danych są odpowiednie do użycia w środowisku Internet i pracy oraz wewnątrz przeglądarki.  
  
-   Należy rozważyć postępu jest przekazywana do kontenera.  
  
     Powiadom kontenera postępu pobierania asynchroniczne, w tym przypadku użytkownik może uruchomić interakcję ze stroną i po ukończeniu pobierania. Kontener można wyświetlić postęp (takie jak procent wykonania) dla użytkownika.  
  
-   Należy wziąć pod uwagę, jak formanty są rejestrowane na komputerze klienckim.  
  
## <a name="creating-a-new-activex-control"></a>Tworzenie nowego formantu ActiveX  
 Podczas tworzenia nowego formantu za pomocą Kreatora aplikacji, można włączyć obsługę monikery asynchroniczne, a także innych optymalizacji. Aby dodać obsługę, aby asynchronicznie pobrać właściwości formantu, wykonaj następujące kroki:  
  
#### <a name="to-create-your-project-using-the-mfc-activex-control-wizard"></a>Aby utworzyć projekt za pomocą Kreatora kontrolki ActiveX MFC  
  
1.  Kliknij przycisk **nowy** na **pliku** menu.  
  
2.  Wybierz **Kreator kontrolek ActiveX MFC** z języka Visual C++ projektów i nazwy projektu.  
  
3.  Na **ustawienia kontroli** wybierz pozycję **asynchronicznie ładuje właściwości**. Wybranie tej opcji skonfigurować właściwości stanie gotowe i zdarzenia zmieniającego stan gotowości.  
  
     Możesz też wybrać inne optymalizacje, takich jak **aktywacji niepowiązanej z oknami**, opisanym w [formantów ActiveX: Optymalizacja](../mfc/mfc-activex-controls-optimization.md).  
  
4.  Wybierz **Zakończ** Aby utworzyć projekt.  
  
#### <a name="to-create-a-class-derived-from-cdatapathproperty"></a>Aby utworzyć klasę pochodzącą od CDataPathProperty  
  
1.  Utwórz klasę pochodną `CDataPathProperty`.  
  
2.  W każdym z plików źródłowych, które zawiera plik nagłówka formantu dodać pliku nagłówka dla tej klasy przed nim.  
  
3.  W tej klasie zastąpienie `OnDataAvailable`. Ta funkcja jest wywoływana, gdy dane są dostępne do wyświetlenia. W miarę wprowadzania danych może obsługiwać dowolny sposób można wybrać, na przykład przez stopniowo renderowaniem go.  
  
     Poniższy fragment kodu jest prosty przykład stopniowo wyświetlanie danych w formancie edycji. Zwróć uwagę na użycie flagi **BSCF_FIRSTDATANOTIFICATION** Wyczyść kontrolki edycji.  
  
     [!code-cpp[NVC_MFCActiveXControl#1](../mfc/codesnippet/cpp/activex-controls-on-the-internet_1.cpp)]  
  
     Należy pamiętać, że musi zawierać AFXCMN. H, aby użyć `CListCtrl` klasy.  
  
4.  Po formantu użytkownika ogólny stan zostanie zmieniony (na przykład z ładowania do zainicjowana lub użytkownika, interaktywny), wywołania `COleControl::InternalSetReadyState`. Jeśli formant ma właściwość path tylko jednego danych, możesz dodać kod na **BSCF_LASTDATANOTIFICATION** powiadomiono kontenera zakończeniu pobierania. Na przykład:  
  
     [!code-cpp[NVC_MFCActiveXControl#2](../mfc/codesnippet/cpp/activex-controls-on-the-internet_2.cpp)]  
  
5.  Zastąpienie `OnProgress`. W `OnProgress`, są przekazywane liczbą przedstawiający maksymalną wielkość zakresu i jest numer przedstawiający, jak daleko wraz z bieżącym pobierania. Te liczby służy do wyświetlania stanu, takie jak procent wykonania dla użytkownika.  
  
 Następna procedura dodaje właściwość do formant do użycia klasy pochodnej po prostu.  
  
#### <a name="to-add-a-property"></a>Aby dodać właściwość  
  
1.  W **widoku klasy**, kliknij prawym przyciskiem myszy interfejs poniżej tego węzła Biblioteka i wybierz **Dodaj**, następnie **Dodaj właściwość**. Spowoduje to uruchomienie **Dodaj Kreatora właściwości**.  
  
2.  W **Dodaj Kreatora właściwości**, wybierz pozycję **metod Set/Get** przycisku radiowego, typ **nazwa właściwości**, na przykład, EditControlText i wybierz BSTR jako **Typ właściwości**.  
  
3.  Kliknij przycisk **Zakończ**.  
  
4.  Deklarowanie zmiennej członkowskiej, z Twojego `CDataPathProperty`-pochodnej klasy do własnej klasy formantu ActiveX.  
  
     [!code-cpp[NVC_MFCActiveXControl#3](../mfc/codesnippet/cpp/activex-controls-on-the-internet_3.h)]  
  
5.  Implementowanie `Get/Set` metody. Aby uzyskać `Get`, zwraca ciąg. Aby uzyskać `Set`, obciążenia właściwości i wywołanie `SetModifiedFlag`.  
  
     [!code-cpp[NVC_MFCActiveXControl#4](../mfc/codesnippet/cpp/activex-controls-on-the-internet_4.cpp)]  
  
6.  W [DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange), Dodaj następujący wiersz:  
  
     [!code-cpp[NVC_MFCActiveXControl#5](../mfc/codesnippet/cpp/activex-controls-on-the-internet_5.cpp)]  
  
7.  Zastąpienie [ResetData](../mfc/reference/cdatapathproperty-class.md#resetdata) powiadomiono właściwość do resetowania jego kontrolą przez dodanie tego wiersza:  
  
     [!code-cpp[NVC_MFCActiveXControl#6](../mfc/codesnippet/cpp/activex-controls-on-the-internet_6.cpp)]  
  
## <a name="deciding-whether-to-derive-from-cdatapathproperty-or-ccacheddatapathproperty"></a>Podjęcie decyzji o CDataPathProperty lub CCachedDataPathProperty  
 Poprzedni przykład opisano kroki tworzenia klasy pochodnej właściwości formantu z `CDataPathProperty`. Jeśli pobierasz danych w czasie rzeczywistym, które często zmienia się i dla których nie trzeba przechowywać wszystkie dane, ale bieżąca wartość jest dobre rozwiązanie. Przykładem jest formantem giełdowych.  
  
 Może również pochodzić z `CCachedDataPathProperty`. W takim przypadku pobrane dane są buforowane w pliku pamięci. To jest dobrym rozwiązaniem, jeśli chcesz zachować wszystkie pobrane dane — na przykład formant, który renderuje stopniowo mapy bitowej. W takim przypadku klasa ma zmiennej członkowskiej z danymi:  
  
 `CMemFile m_Cache;`  
  
 W Twojej klasy kontrolki ActiveX, można użyć tego pliku mapowanego pamięci w `OnDraw` do wyświetlania danych. Formantu ActiveX `CCachedDataPathProperty`-klasy, Zastąp funkcji członkowskiej `OnDataAvailable` akcji i unieważnić formantu, po wywołaniu metody implementacji klasy podstawowej.  
  
 [!code-cpp[NVC_MFCActiveXControl#7](../mfc/codesnippet/cpp/activex-controls-on-the-internet_7.cpp)]  
  
## <a name="downloading-data-asynchronously-using-activex-controls"></a>Pobieranie danych asynchronicznie za pomocą formantów ActiveX  
 Pobieranie danych za pośrednictwem sieci powinno być wykonywane asynchronicznie. Zaletą takiego więc jest to, że jeśli transferu dużej ilości danych lub, jeśli połączenie jest powolne, proces pobierania nie powoduje blokowania innych procesów na komputerze klienckim.  
  
 Monikery asynchroniczne umożliwiają asynchronicznie pobierania danych przez sieć. Operacja odczytu asynchronicznego moniker zwraca natychmiast, nawet wtedy, gdy operacja nie została ukończona.  
  
 Na przykład jeśli tylko 10 bajtów są dostępne i odczytu jest wywoływana asynchronicznie w pliku 1K, odczytu nie są blokowane, ale zwraca z aktualnie dostępnych bajtów 10.  
  
 Można zaimplementować [monikery asynchroniczne](../mfc/asynchronous-monikers-on-the-internet.md) przy użyciu `CAsyncMonikerFile` klasy. Jednak można używać formantów ActiveX `CDataPathProperty` klasy, która jest pochodną `CAsyncMonikerFile`, pomagających w realizacji właściwości asynchronicznej formantu.  
  
 Przykładowe ASYNDOWN pokazano, jak skonfigurować pętli asynchronicznego odczytywania danych przy użyciu czasomierze. ASYNDOWN opisano szczegółowo w artykule bazy wiedzy Knowledge Base "Porada: AsyncDown pokazuje asynchroniczne danych Pobierz" (Q177244) i jest dostępny do pobrania firmy Microsoft Download Center. (Aby uzyskać więcej informacji na temat pobierania plików z Microsoft Download Center, zobacz artykuł "Jak można uzyskać obsługi plików z usługi Online firmy Microsoft" (Q119591) w bazie wiedzy Microsoft Knowledge Base.) Można znaleźć artykuły bazy wiedzy w [ http://support.microsoft.com/support ](http://support.microsoft.com/support).  
  
 Podstawowe zastosowanych w ASYNDOWN jest skonfigurowanie czasomierz **CDataPathProperty::OnDataAvailable** wskazująca, kiedy dane są dostępne. Po otrzymaniu komunikatu czasomierza aplikacji odczytuje w blokach 128 bajtów danych i wypełnia kontrolkę edycji. Jeśli dane nie są dostępne podczas obsługi komunikatu czasomierza, czasomierz jest wyłączona. `OnDataAvailable` powoduje włączenie czasomierza, jeśli później większej ilości danych.  
  
## <a name="displaying-a-control-on-a-web-page"></a>Wyświetlanie formantu na stronie sieci Web  
 Oto przykład tagu object i atrybuty Wstawianie kontrolki na stronie sieci Web.  
  
 `<OBJECT`  
  
 `CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"`  
  
 `CODEBASE="/ie/download/activex/iechart.ocx"`  
  
 `ID=chart1`  
  
 `WIDTH=400`  
  
 `HEIGHT=200`  
  
 `ALIGN=center`  
  
 `HSPACE=0`  
  
 `VSPACE=0`  
  
 `>`  
  
 `<PARAM NAME="BackColor" value="#ffffff">`  
  
 `<PARAM NAME="ForeColor" value="#0000ff">`  
  
 `<PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt">`  
  
 `</OBJECT>`  
  
## <a name="updating-an-existing-ole-control-to-use-new-activex-control-features"></a>Uaktualnianie istniejącego formantu OLE do korzystania z nowych funkcji formantu ActiveX  
 Jeśli formantu OLE została utworzona z wersją programu Visual C++ przed 4.2, istnieją czynności, które należy wykonać w celu zwiększenia wydajności i rozszerzają jego funkcjonalność. Szczegółowe omówienie tych zmian, zobacz [formantów ActiveX: Optymalizacja](../mfc/mfc-activex-controls-optimization.md).  
  
 Jeśli dodajesz właściwości asynchronicznej obsługi do istniejącego formantu, należy dodać właściwość stanie gotowe i `ReadyStateChange` zdarzeń samodzielnie. W Konstruktorze dla formantu należy dodać:  
  
 [!code-cpp[NVC_MFCActiveXControl#8](../mfc/codesnippet/cpp/activex-controls-on-the-internet_8.cpp)]  
  
 Spowoduje zaktualizowanie stanu gotowości, ponieważ kod jest pobierana przez wywołanie metody [COleControl::InternalSetReadyState](../mfc/reference/colecontrol-class.md#internalsetreadystate). W jednym miejscu, można wywołać `InternalSetReadyState` z `OnProgress` zastąpienie `CDataPathProperty`-klasy.  
  

  
## <a name="see-also"></a>Zobacz też  
 [Zadania związane z programowaniem Internetu MFC](../mfc/mfc-internet-programming-tasks.md)   
 [MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)

