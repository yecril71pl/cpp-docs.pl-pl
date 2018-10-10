---
title: Kontrolki ActiveX w Internecie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2018
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
ms.openlocfilehash: 6004c3acd052d1424004017941a5e4aa110c602c
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890339"
---
# <a name="activex-controls-on-the-internet"></a>Kontrolki ActiveX w Internecie

Formanty ActiveX to zaktualizowaną wersję specyfikacji sterowania OLE.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji, zobacz [formantów ActiveX](activex-controls.md).

Formanty są podstawowej architektury do tworzenia składników oprogramowania programowalne, których można użyć w wielu różnych kontenerów, w tym przeglądarki sieci Web obsługującej COM w Internecie. Formantu ActiveX może być kontrolka w postaci Internet i można dodać jej funkcjonalność do aktywnego dokumentu lub być częścią strony sieci Web. Formanty na stronie sieci Web mogą komunikować się ze sobą przy użyciu skryptów.

Formanty ActiveX nie są ograniczone do Internetu. Kontrolki ActiveX można również w dowolnym kontenerze, tak długo, jak są obsługiwane przez kontrolkę interfejsy wymagane przez tego kontenera.

**Kontrolki ActiveX ma kilka zalet, w tym:**

- Mniej wymagane interfejsy niż poprzednie formantów OLE.

- Może zostać bez okien i zawsze aktywny w miejscu.

**W celu formantu ActiveX, formant musi:**

- Obsługa `IUnknown` interfejsu.

- Być obiektem COM.

- Eksportuj **DLLRegisterServer** i **DLLUnRegisterServer**.

- Obsługuje dodatkowe interfejsy, zgodnie z potrzebami dla funkcji.

## <a name="making-your-existing-controls-internet-friendly"></a>Tworzenie usługi istniejących formantów przyjaznego dla Internetu

Projektowanie kontrolki, które będą działać poprawnie w środowisku sieci Internet wymaga zaplanowania małą szybkością w Internecie. Możesz użyć istniejących formantów; istnieją kroki, które należy podjąć, aby zmniejszyć rozmiar kodu, a aby asynchronicznie pobrać właściwości formantu.

Aby poprawić wydajność dla Twoich kontrolek, wykonaj te porady dotyczące zagadnienia dotyczące wydajności:

- Implementowanie metod opisanych w artykule [kontrolek ActiveX: Optymalizacja](../mfc/mfc-activex-controls-optimization.md).

- Należy wziąć pod uwagę, jak formant zostanie uruchomiony.

- Być asynchroniczne; nie wstrzymać innych programów.

- Pobieranie danych w małych blokach.

     Podczas pobierania dużych strumieni, takich jak mapy bitowe lub dane wideo, dostęp do danych kontrolki asynchronicznie we współpracy z kontenera. Pobieranie danych w sposób przyrostowego lub progresywnego pracy wspólnie z innymi formantami, które mogą również pobieranie danych. Kod można również odbywać się pobieranie asynchronicznie.

- Pobierz kod i właściwości w tle.

- Stają się interfejs użytkownika active tak szybko, jak to możliwe.

- Należy wziąć pod uwagę sposób trwałe dane są przechowywane, zarówno właściwości, jak i dużych ilości danych obiektów blob (takie jak mapy bitowej obraz lub film wideo danych).

     Formanty z znacznej ilości trwałych danych, takich jak duże mapy bitowe lub plikach AVI wymagają uważnego pobieranie metody. Dokumentu lub strony można tak szybko, jak to możliwe staje się widoczny i umożliwia użytkownikowi interakcję ze stroną, podczas kontroli pobierania danych w tle.

- Napisz efektywne procedury rozmiar kodu i czas wykonywania w dół.

     Małych kontrolek przycisków i etykiet, za pomocą tylko kilku bajtów danych trwałych, są odpowiednie do użycia w środowisku Internet i pracy również wewnątrz przeglądarki.

- Należy wziąć pod uwagę, że postęp jest przekazywane do kontenera.

     Powiadom kontenera postępu do pobrania asynchronicznego, takich jak po użytkownik może uruchomić do interakcji ze strony i pobranie zostanie ukończone. Kontener można wyświetlić postęp (takie jak procent ukończenia) dla użytkownika.

- Należy wziąć pod uwagę, jak formanty są rejestrowane na komputerze klienckim.

## <a name="creating-a-new-activex-control"></a>Tworzenie nowego formantu ActiveX

Podczas tworzenia nowego formantu za pomocą Kreatora aplikacji, można włączyć obsługę monikerów asynchronicznych, a także inne optymalizacje. Aby dodać obsługę, aby asynchronicznie pobrać właściwości formantu, wykonaj następujące kroki:

#### <a name="to-create-your-project-using-the-mfc-activex-control-wizard"></a>Aby utworzyć projekt za pomocą Kreatora kontrolek ActiveX MFC

1. Kliknij przycisk **New** na **pliku** menu.

1. Wybierz **Kreator kontrolek ActiveX MFC** z Visual C++ projektów i nazwij swój projekt.

1. Na **ustawienia kontroli** wybierz opcję **ładuje asynchronicznie właściwości**. Wybranie tej opcji ustawia się właściwości stanu gotowości i zdarzenia zmieniającego stan gotowości za Ciebie.

     Możesz również wybrać inne optymalizacje, takie jak **aktywacji niepowiązanej z oknami**, który jest opisany w [kontrolek ActiveX: Optymalizacja](../mfc/mfc-activex-controls-optimization.md).

1. Wybierz **Zakończ** do tworzenia projektu.

#### <a name="to-create-a-class-derived-from-cdatapathproperty"></a>Aby utworzyć klasę pochodną CDataPathProperty

1. Utwórz klasę pochodną `CDataPathProperty`.

1. W każdym z plików źródłowych, które dołącza plik nagłówkowy dla kontrolki należy dodać plik nagłówkowy dla tej klasy przed nią.

1. W tej klasie zastąpić `OnDataAvailable`. Ta funkcja jest wywoływana zawsze wtedy, gdy dane są dostępne do wyświetlenia. Danych staje się dostępne, może obsłużyć dowolny sposób, który wybierzesz, na przykład przez stopniowe renderowaniem go.

     Poniższy fragment kodu jest prosty przykład stopniowo wyświetlanie danych w formancie edycji. Zwróć uwagę na użycie flagi **BSCF_FIRSTDATANOTIFICATION** Wyczyść kontrolki edycji.

     [!code-cpp[NVC_MFCActiveXControl#1](../mfc/codesnippet/cpp/activex-controls-on-the-internet_1.cpp)]

     Należy pamiętać, że musi zawierać AFXCMN. H, aby użyć `CListCtrl` klasy.

1. Podczas kontroli nad jego ogólną stan zmieni się (na przykład z ładowanie do zainicjowane lub użytkownika interakcyjnego), wywołanie `COleControl::InternalSetReadyState`. Jeśli formant ma właściwości ścieżki danych tylko jeden, możesz dodać kod na **BSCF_LASTDATANOTIFICATION** powiadomić kontenera o ukończeniu pobierania. Na przykład:

     [!code-cpp[NVC_MFCActiveXControl#2](../mfc/codesnippet/cpp/activex-controls-on-the-internet_2.cpp)]

1. Zastąp `OnProgress`. W `OnProgress`, są przekazywane liczbą przedstawiający maksymalną wielkość zakresu i jest liczba pokazujący, jak daleko u bieżącej pobierania. Aby wyświetlić stan, takie jak procent wykonania dla użytkownika, można użyć tych liczb.

Następna procedura dodaje właściwość do kontroli na korzystanie z klasy pochodnej po prostu.

#### <a name="to-add-a-property"></a>Aby dodać właściwość

1. W **Widok klas**, kliknij prawym przyciskiem myszy interfejs poniżej tego węzła Biblioteka i wybierz **Dodaj**, następnie **Dodaj właściwość**. Spowoduje to uruchomienie **Kreator dodawania właściwości**.

1. W **Kreator dodawania właściwości**, wybierz opcję **metod Set/Get** przycisk radiowy, typ **nazwa właściwości**, na przykład, EditControlText i wybierz BSTR jako **Typ właściwości**.

1. Kliknij przycisk **Zakończ**.

1. Zadeklaruj zmienną członkowską z Twojej `CDataPathProperty`-klasy pochodnej do klasy kontrolki ActiveX.

     [!code-cpp[NVC_MFCActiveXControl#3](../mfc/codesnippet/cpp/activex-controls-on-the-internet_3.h)]

1. Implementowanie `Get/Set` metody. Aby uzyskać `Get`, zwróć ciąg. Aby uzyskać `Set`, załaduj właściwości i wywołania `SetModifiedFlag`.

     [!code-cpp[NVC_MFCActiveXControl#4](../mfc/codesnippet/cpp/activex-controls-on-the-internet_4.cpp)]

1. W [DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange), Dodaj następujący wiersz:

     [!code-cpp[NVC_MFCActiveXControl#5](../mfc/codesnippet/cpp/activex-controls-on-the-internet_5.cpp)]

1. Zastąp [ResetData](../mfc/reference/cdatapathproperty-class.md#resetdata) powiadomić właściwości można zresetować do jego kontrolki, dodając ten wiersz:

     [!code-cpp[NVC_MFCActiveXControl#6](../mfc/codesnippet/cpp/activex-controls-on-the-internet_6.cpp)]

## <a name="deciding-whether-to-derive-from-cdatapathproperty-or-ccacheddatapathproperty"></a>Podjęcie decyzji o dziedziczyć CDataPathProperty lub CCachedDataPathProperty

Poprzedni przykład w tym artykule opisano kroki wyprowadzanie właściwość kontroli nad `CDataPathProperty`. Jest to dobry wybór, jeśli pobierasz dane w czasie rzeczywistym, które często zmieniają się i dla których nie potrzebujesz do zachowania wszystkich danych, ale tylko bieżącą wartość. Przykładem jest formantem giełdowej.

Można również dziedziczyć `CCachedDataPathProperty`. W tym przypadku pobrane dane są buforowane w pliku pamięci. Jest to dobry wybór, jeśli potrzebujesz do przechowywania pobranych danych — na przykład formant, który stopniowo powoduje wyświetlenie mapy bitowej. W takim przypadku klasa ma zmienną członkowską zawierających dane użytkownika:

`CMemFile m_Cache;`

W klasie kontrolki ActiveX, można użyć tego pliku mapowanego pamięci w `OnDraw` do wyświetlania danych. W kontrolce ActiveX `CCachedDataPathProperty`-klasy pochodnej przesłonić funkcji elementu członkowskiego `OnDataAvailable` i unieważnić kontrolki, po wywołaniu implementacji klasy podstawowej.

[!code-cpp[NVC_MFCActiveXControl#7](../mfc/codesnippet/cpp/activex-controls-on-the-internet_7.cpp)]

## <a name="downloading-data-asynchronously-using-activex-controls"></a>Pobieranie danych asynchronicznie za pomocą kontrolki ActiveX

Pobieranie danych przez sieć powinna być wykonywana asynchronicznie. Zaletą spowoduje więc jest to, że jeśli przesyłaną dużej ilości danych lub jeśli połączenie jest powolne, proces pobierania nie będzie blokować innych procesów na komputerze klienckim.

Monikery asynchroniczne umożliwiają podczas pobierania danych asynchronicznie za pośrednictwem sieci. Operację odczytu asynchronicznego moniker zwraca wynik natychmiast, nawet wtedy, gdy operacja nie została zakończona.

Na przykład jeśli tylko 10 bajtów są dostępne i odczytu nosi nazwę asynchronicznej w pliku 1K, odczytu nie są blokowane, ale zwraca aktualnie dostępne 10 bajtów.

Możesz wdrożyć [monikerów asynchronicznych](../mfc/asynchronous-monikers-on-the-internet.md) przy użyciu `CAsyncMonikerFile` klasy. Jednak można użyć kontrolek ActiveX `CDataPathProperty` klasy, która jest pochodną `CAsyncMonikerFile`, pomagających w realizacji właściwości kontrolki asynchronicznego.

## <a name="displaying-a-control-on-a-web-page"></a>Wyświetlanie kontrolki na stronie sieci Web

Oto przykład potraktowane jak tag obiektów i atrybutów Wstawianie kontrolki na stronie sieci Web.

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

## <a name="updating-an-existing-ole-control-to-use-new-activex-control-features"></a>Aktualizowanie istniejącej kontrolki OLE, aby korzystać z nowych funkcji kontrolek ActiveX

Jeśli kontrolki OLE został utworzony przy użyciu wersji środowiska Visual C++ przed 4.2, istnieją kroki, które można wykonać w celu zwiększenia wydajności i ulepszanie jego funkcji. Aby uzyskać szczegółowe omówienie tych zmian, zobacz [kontrolek ActiveX: Optymalizacja](../mfc/mfc-activex-controls-optimization.md).

W przypadku dodawania obsługi asynchronicznego właściwości do istniejącego formantu, musisz dodać właściwość stanu gotowości i `ReadyStateChange` zdarzeń samodzielnie. W Konstruktorze kontrolki należy dodać:

[!code-cpp[NVC_MFCActiveXControl#8](../mfc/codesnippet/cpp/activex-controls-on-the-internet_8.cpp)]

Spowoduje zaktualizowanie stanu gotowości, jak kod jest pobierany przez wywołanie metody [COleControl::InternalSetReadyState](../mfc/reference/colecontrol-class.md#internalsetreadystate). Jednym miejscu, można wywołać `InternalSetReadyState` pochodzi z `OnProgress` zastępowania `CDataPathProperty`-klasy pochodnej.



## <a name="see-also"></a>Zobacz też

[MFC — zadania związane z programowaniem Internetu](../mfc/mfc-internet-programming-tasks.md)<br/>
[MFC — podstawy programowania Internetu](../mfc/mfc-internet-programming-basics.md)

