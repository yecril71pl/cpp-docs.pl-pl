---
title: Formanty ActiveX w Internecie
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], creating
- ActiveX controls [MFC], Internet
- downloading data with ActiveX controls
- OLE controls [MFC], upgrading to ActiveX
- Internet applications [MFC], ActiveX controls
- networks [MFC], downloading with ActiveX controls
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
ms.openlocfilehash: f06a6f6f71e922163fd95c59836c50b88b05ed3a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616481"
---
# <a name="activex-controls-on-the-internet"></a>Formanty ActiveX w Internecie

Kontrolki ActiveX są zaktualizowaną wersją specyfikacji formantu OLE.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX](activex-controls.md).

Formanty stanowią podstawową architekturę do tworzenia programowalnych składników oprogramowania, które mogą być używane w różnych kontenerach, w tym przeglądarki sieci Web obsługujące COM w Internecie. Każda Kontrolka ActiveX może być kontrolką internetową i może dodawać jej funkcje do aktywnego dokumentu lub być częścią strony sieci Web. Kontrolki na stronie sieci Web mogą komunikować się ze sobą przy użyciu skryptów.

Kontrolki ActiveX nie są ograniczone do Internetu. Kontrolka ActiveX może być również używana w dowolnym kontenerze, o ile formant obsługuje interfejsy wymagane przez ten kontener.

**Kontrolki ActiveX mają kilka korzyści, w tym:**

- Mniej wymagane interfejsy niż poprzednie kontrolki OLE.

- Możliwość korzystania z funkcji bezokienkowej i zawsze aktywnej.

**Aby można było sterować kontrolką ActiveX, formant musi:**

- Obsługa `IUnknown` interfejsu.

- Być obiektem COM.

- Eksportuj **DllRegisterServer** i **DllUnregisterServer**.

- Obsługa dodatkowych interfejsów w miarę potrzeby w zakresie funkcjonalności.

## <a name="making-your-existing-controls-internet-friendly"></a>Udostępnianie istniejących kontrolek przyjaznych dla Internetu

Projektowanie kontrolki, która będzie działała prawidłowo w środowisku internetowym, wymaga uwzględnienia stosunkowo niskich szybkości transmisji w Internecie. Możesz użyć istniejących kontrolek. Istnieją jednak kroki, które należy wykonać, aby zmniejszyć rozmiar kodu i zapewnić, że właściwości kontrolki będą pobierane asynchronicznie.

Aby zwiększyć wydajność kontrolek, postępuj zgodnie z poniższymi wskazówkami dotyczącymi wydajności:

- Zaimplementuj techniki opisane w artykule [kontrolki ActiveX: Optymalizacja](mfc-activex-controls-optimization.md).

- Należy wziąć pod uwagę sposób tworzenia wystąpienia kontrolki.

- Być asynchroniczne; nie należy przechowywać innych programów.

- Pobierz dane w małych blokach.

   Podczas pobierania dużych strumieni, takich jak mapy bitowe lub dane wideo, można w sposób asynchroniczny uzyskać dostęp do danych kontrolki we współpracy z kontenerem. Pobierz dane w przyrostowym lub progresywnym czasie, pracując wspólnie z innymi kontrolkami, które mogą również pobierać dane. Kod można także pobrać asynchronicznie.

- Pobierz kod i właściwości w tle.

- Czy interfejs użytkownika jest aktywny, tak szybko, jak to możliwe.

- Zastanów się, jak są przechowywane trwałe dane, zarówno właściwości, jak i duże obiekty BLOB danych (takie jak obraz mapy bitowej lub dane wideo).

   Kontroluje znaczną ilość danych trwałych, takich jak duże mapy bitowe lub pliki AVI, wymagają starannej uwagi na pobranie metody. Dokument lub strona mogą stać się widoczne tak szybko, jak to możliwe, i umożliwia użytkownikowi współpracującie ze stroną, podczas gdy kontrolki pobierają dane w tle.

- Zapisuj wydajne procedury w celu zachowania rozmiaru kodu i czasu uruchamiania.

   Małe kontrolki przycisków i etykiet z tylko kilkoma bajtami danych trwałych są odpowiednie do użycia w środowisku internetowym i w przeglądarkach.

- Należy wziąć pod uwagę postęp komunikacji z kontenerem.

   Powiadom kontener postępu w asynchronicznym pobieraniu, w tym, gdy użytkownik może rozpocząć pracę ze stroną i po zakończeniu pobierania. Kontener może wyświetlać postęp (na przykład procent wykonania) dla użytkownika.

- Należy rozważyć sposób rejestracji formantów na komputerze klienckim.

## <a name="creating-a-new-activex-control"></a>Tworzenie nowej kontrolki ActiveX

Podczas tworzenia nowej kontrolki za pomocą Kreatora aplikacji można włączyć obsługę monikerów asynchronicznych oraz inne optymalizacje. Aby dodać obsługę do pobierania właściwości kontrolek asynchronicznie, wykonaj następujące czynności:

#### <a name="to-create-your-project-using-the-mfc-activex-control-wizard"></a>Aby utworzyć projekt przy użyciu kreatora kontrolki ActiveX MFC

1. Kliknij pozycję **Nowy** w menu **plik** .

1. Wybierz **Kreatora formantów ActiveX MFC** z projektów Visual Studio C++ i Nadaj projektowi nazwę.

1. Na stronie **Ustawienia kontroli** wybierz pozycję **Załaduj właściwości asynchronicznie**. Wybranie tej opcji powoduje skonfigurowanie właściwości stan gotowe oraz zdarzenia zmiany stanu gotowości.

   Można również wybrać inne optymalizacje, takie jak **Aktywacja bez okien**, która jest opisana w [kontrolkach ActiveX: Optymalizacja](mfc-activex-controls-optimization.md).

1. Wybierz pozycję **Zakończ** , aby utworzyć projekt.

#### <a name="to-create-a-class-derived-from-cdatapathproperty"></a>Aby utworzyć klasę pochodną CDataPathProperty

1. Utwórz klasę pochodną `CDataPathProperty` .

1. W każdym z plików źródłowych, które zawierają plik nagłówkowy kontrolki, Dodaj do niej plik nagłówkowy dla tej klasy.

1. W tej klasie Przesłoń `OnDataAvailable` . Ta funkcja jest wywoływana za każdym razem, gdy dane są dostępne do wyświetlenia. Gdy dane staną się dostępne, możesz je obsłużyć w dowolny sposób, na przykład przez stopniowe renderowanie.

   Poniższy fragment kodu jest prostym przykładem progresywnego wyświetlania danych w kontrolce edycji. Zwróć uwagę na użycie flagi **BSCF_FIRSTDATANOTIFICATION** , aby wyczyścić kontrolkę Edycja.

   [!code-cpp[NVC_MFCActiveXControl#1](codesnippet/cpp/activex-controls-on-the-internet_1.cpp)]

   Należy pamiętać, że należy uwzględnić AFXCMN. H, aby użyć `CListCtrl` klasy.

1. Po zmianie ogólnego stanu kontrolki (na przykład w przypadku ładowania do zainicjowany lub interaktywnego użytkownika) Wywołaj polecenie `COleControl::InternalSetReadyState` . Jeśli kontrolka ma tylko jedną właściwość Path, można dodać kod na **BSCF_LASTDATANOTIFICATION** , aby powiadomić kontener o zakończeniu pobierania. Przykład:

   [!code-cpp[NVC_MFCActiveXControl#2](codesnippet/cpp/activex-controls-on-the-internet_2.cpp)]

1. Zastąpienie `OnProgress` . W programie `OnProgress` przeszedł numer pokazujący maksymalny zakres i liczbę pokazującą, jak daleko od bieżącego pobierania. Możesz użyć tych liczb, aby wyświetlić stan, na przykład procent wykonania dla użytkownika.

Następna procedura dodaje do kontrolki właściwość, aby użyć klasy pochodnej.

#### <a name="to-add-a-property"></a>Aby dodać właściwość

1. W **Widok klasy**kliknij prawym przyciskiem myszy interfejs pod węzłem biblioteki i wybierz polecenie **Dodaj**, a następnie **Dodaj właściwość**. Spowoduje to uruchomienie **Kreatora dodawania właściwości**.

1. W **Kreatorze dodawania właściwości**wybierz przycisk radiowy **Ustaw/Pobierz metody** , wpisz **nazwę właściwości**, na przykład EditControlText, a następnie wybierz BSTR jako **Typ właściwości**.

1. Kliknij przycisk **Zakończ**.

1. Zadeklaruj zmienną składową `CDataPathProperty` klasy pochodnej dla klasy kontrolki ActiveX.

   [!code-cpp[NVC_MFCActiveXControl#3](codesnippet/cpp/activex-controls-on-the-internet_3.h)]

1. Zaimplementuj `Get/Set` metody. Dla `Get` zwraca ciąg. W przypadku `Set` , Załaduj Właściwość i wywołanie `SetModifiedFlag` .

   [!code-cpp[NVC_MFCActiveXControl#4](codesnippet/cpp/activex-controls-on-the-internet_4.cpp)]

1. W [DoPropExchange](reference/colecontrol-class.md#dopropexchange)Dodaj następujący wiersz:

   [!code-cpp[NVC_MFCActiveXControl#5](codesnippet/cpp/activex-controls-on-the-internet_5.cpp)]

1. Przesłoń [operację](reference/cdatapathproperty-class.md#resetdata) przywracania, aby powiadomić właściwość o zresetowaniu jej kontrolki przez dodanie tego wiersza:

   [!code-cpp[NVC_MFCActiveXControl#6](codesnippet/cpp/activex-controls-on-the-internet_6.cpp)]

## <a name="deciding-whether-to-derive-from-cdatapathproperty-or-ccacheddatapathproperty"></a>Decydowanie o tym, czy dziedziczyć z CDataPathProperty, czy CCachedDataPathProperty

W poprzednim przykładzie przedstawiono procedurę wyprowadzania właściwości kontrolki z `CDataPathProperty` . Jest to dobry wybór w przypadku pobierania danych w czasie rzeczywistym, które często zmieniają się i dla których nie ma potrzeby przechowywania wszystkich danych, ale tylko bieżącej wartości. Przykładem jest kontrolka giełdowa.

Można również utworzyć od `CCachedDataPathProperty` . W takim przypadku pobrane dane są buforowane w pliku pamięci. Jest to dobry wybór, jeśli trzeba zachować wszystkie pobrane dane — na przykład kontrolka, która stopniowo renderuje mapę bitową. W takim przypadku Klasa ma zmienną członkowską zawierającą dane:

`CMemFile m_Cache;`

W klasie kontrolki ActiveX można użyć tego pliku mapowanego w pamięci w programie, `OnDraw` Aby wyświetlić dane. W klasie pochodnej kontrolki ActiveX `CCachedDataPathProperty` Przesłoń funkcję członkowską `OnDataAvailable` i Unieważnij formant, po wywołaniu implementacji klasy podstawowej.

[!code-cpp[NVC_MFCActiveXControl#7](codesnippet/cpp/activex-controls-on-the-internet_7.cpp)]

## <a name="downloading-data-asynchronously-using-activex-controls"></a>Asynchroniczne pobieranie danych za pomocą kontrolek ActiveX

Pobieranie danych za pośrednictwem sieci powinno odbywać się asynchronicznie. Zaletą tej metody jest to, że w przypadku przesyłania dużej ilości danych lub w przypadku powolnego połączenia proces pobierania nie będzie blokować innych procesów na kliencie.

Monikery asynchroniczne umożliwiają pobieranie danych asynchronicznie za pośrednictwem sieci. Operacja odczytu na asynchronicznej monikerze zwraca natychmiast, nawet jeśli operacja nie została ukończona.

Na przykład, jeśli dostępne są tylko 10 bajtów, a odczyt jest wywoływany asynchronicznie w pliku z 1K, odczyt nie jest blokowany, ale zwraca z aktualnie dostępnym 10 bajtem.

[Monikery asynchroniczne](asynchronous-monikers-on-the-internet.md) są implementowane przy użyciu `CAsyncMonikerFile` klasy. Jednak kontrolki ActiveX mogą korzystać z `CDataPathProperty` klasy, która pochodzi od `CAsyncMonikerFile` , aby pomóc zaimplementować właściwości kontroli asynchronicznej.

## <a name="displaying-a-control-on-a-web-page"></a>Wyświetlanie kontrolki na stronie sieci Web

Oto przykład znacznika obiektu i atrybutów wstawiania kontrolki na stronie sieci Web.

```xml
<OBJECT
  CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"
  CODEBASE="/ie/download/activex/iechart.ocx"
  ID=chart1
  WIDTH=400
  HEIGHT=200
  ALIGN=center
  HSPACE=0
  VSPACE=0>
  <PARAM NAME="BackColor" value="#ffffff"/>
  <PARAM NAME="ForeColor" value="#0000ff"/>
  <PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt"/>
</OBJECT>
```

## <a name="updating-an-existing-ole-control-to-use-new-activex-control-features"></a>Aktualizowanie istniejącej kontrolki OLE do korzystania z nowych funkcji kontrolek ActiveX

Jeśli kontrolka OLE została utworzona przy użyciu wersji Visual C++ wcześniejszej niż 4,2, istnieją kroki, które należy wykonać w celu poprawienia wydajności i zwiększenia jej funkcjonalności. Aby uzyskać szczegółowe omówienie tych zmian, zobacz [kontrolki ActiveX: Optymalizacja](mfc-activex-controls-optimization.md).

Jeśli dodajesz obsługę właściwości asynchronicznych do istniejącej kontrolki, musisz samodzielnie dodać właściwość stan gotowości i `ReadyStateChange` zdarzenie. W konstruktorze kontrolki Dodaj:

[!code-cpp[NVC_MFCActiveXControl#8](codesnippet/cpp/activex-controls-on-the-internet_8.cpp)]

Stan gotowości zostanie zaktualizowany w miarę pobierania kodu przez wywołanie [COleControl:: InternalSetReadyState](reference/colecontrol-class.md#internalsetreadystate). Jedno miejsce, które można wywołać `InternalSetReadyState` , pochodzi z `OnProgress` przesłonięcia `CDataPathProperty` klasy pochodnej.

## <a name="see-also"></a>Zobacz też

[MFC — zadania związane z programowaniem Internetu](mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](mfc-internet-programming-basics.md)
