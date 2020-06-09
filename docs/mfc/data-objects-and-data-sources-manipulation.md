---
title: 'Obiekty danych i źródła danych: operowanie'
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], manipulating
- data sources [MFC], data operations
- data sources [MFC], inserting data
- Clipboard [MFC], determining available formats
- OLE [MFC], data objects
- Clipboard [MFC], passing format information
- data sources [MFC], determining available formats
- delayed rendering [MFC]
- OLE [MFC], data sources
ms.assetid: f7f27e77-bb5d-4131-b819-d71bf929ebaf
ms.openlocfilehash: f1a83511edbf240d9a05d6d489f6cda9453ccea9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620398"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Obiekty danych i źródła danych: operowanie

Po utworzeniu obiektu danych lub źródła danych można wykonać kilka typowych operacji na danych, takich jak wstawianie i usuwanie danych, wyliczanie formatów, w których znajdują się dane, i inne. W tym artykule opisano techniki niezbędne do wykonania najbardziej typowych operacji. Tematy obejmują:

- [Wstawianie danych do źródła danych](#_core_inserting_data_into_a_data_source)

- [Określanie formatów dostępnych w obiekcie danych](#_core_determining_the_formats_available_in_a_data_object)

- [Pobieranie danych z obiektu danych](#_core_retrieving_data_from_a_data_object)

## <a name="inserting-data-into-a-data-source"></a><a name="_core_inserting_data_into_a_data_source"></a>Wstawianie danych do źródła danych

Sposób wstawiania danych do źródła danych zależy od tego, czy dane są dostarczane bezpośrednio, czy na żądanie, i w którym dostarczanym nośniku. Te możliwości są następujące.

### <a name="supplying-data-immediately-immediate-rendering"></a>Dostarczanie danych natychmiast (bezpośrednie renderowanie)

- Wywołaj `COleDataSource::CacheGlobalData` wielokrotnie dla każdego formatu Schowka, w którym dane są dostarczane. Przekaż format schowka, który ma być używany, dojście do pamięci zawierającej dane i, opcjonalnie, strukturę **FORMATETC** opisującą dane.

     -lub-

- Jeśli chcesz bezpośrednio współpracować ze strukturami **STGMEDIUM** , możesz wywołać `COleDataSource::CacheData` zamiast `COleDataSource::CacheGlobalData` w powyższej opcji.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Dostarczanie danych na żądanie (opóźnione renderowanie)

To jest zaawansowany temat.

- Wywołaj `COleDataSource::DelayRenderData` wielokrotnie dla każdego formatu Schowka, w którym dane są dostarczane. Przekaż format schowka, aby można było go używać i opcjonalnie **FORMATETC** strukturę opisującą dane. Gdy dane są żądane, struktura będzie wywoływała `COleDataSource::OnRenderData` , która musi zostać przesłonięta.

     -lub-

- Jeśli używasz `CFile` obiektu do dostarczania danych, wywołaj `COleDataSource::DelayRenderFileData` zamiast `COleDataSource::DelayRenderData` w poprzedniej opcji. Gdy dane są żądane, struktura będzie wywoływała `COleDataSource::OnRenderFileData` , która musi zostać przesłonięta.

## <a name="determining-the-formats-available-in-a-data-object"></a><a name="_core_determining_the_formats_available_in_a_data_object"></a>Określanie formatów dostępnych w obiekcie danych

Aby użytkownik mógł wkleić do niego dane, musi wiedzieć, czy w schowku znajdują się formaty, które może obsłużyć. W tym celu aplikacja powinna wykonać następujące czynności:

1. Utwórz `COleDataObject` obiekt i strukturę **FORMATETC** .

1. Wywołaj `AttachClipboard` funkcję członkowską obiektu danych, aby skojarzyć obiekt danych z danymi w Schowku.

1. Wykonaj jedną z następujących czynności:

   - Wywołaj `IsDataAvailable` funkcję członkowską obiektu danych, jeśli jest wymagany tylko jeden lub dwa formaty. Pozwoli to zaoszczędzić czas w przypadkach, gdy dane w schowku obsługują znacznie więcej formatów niż aplikacja.

     \-oraz

   - Wywołaj `BeginEnumFormats` funkcję członkowską obiektu danych, aby rozpocząć wyliczanie formatów dostępnych w Schowku. Następnie Wywołaj `GetNextFormat` do momentu, gdy schowek zwróci format obsługiwany przez aplikację lub nie ma więcej formatów.

Jeśli używasz **ON_UPDATE_COMMAND_UI**, możesz teraz włączyć opcję Wklej i, ewentualnie Wklej elementy specjalne w menu Edycja. W tym celu należy wywołać metodę `CMenu::EnableMenuItem` or lub `CCmdUI::Enable` . Aby uzyskać więcej informacji na temat aplikacji kontenera, które powinny być wykonywane z elementami menu i, zobacz [menu i zasoby: Dodatki do kontenera](menus-and-resources-container-additions.md).

## <a name="retrieving-data-from-a-data-object"></a><a name="_core_retrieving_data_from_a_data_object"></a>Pobieranie danych z obiektu danych

Gdy użytkownik zdecyduje się na format danych, wszystko to, co pozostanie na pobranie danych z obiektu danych. W tym celu użytkownik decyduje, gdzie umieścić dane, a aplikacja wywołuje odpowiednią funkcję. Dane będą dostępne w jednym z następujących nośników:

|Średniaa|Funkcja do wywołania|
|------------|----------------------|
|Pamięć globalna ( `HGLOBAL` )|`COleDataObject::GetGlobalData`|
|Plik ( `CFile` )|`COleDataObject::GetFileData`|
|Struktura **STGMEDIUM** ( `IStorage` )|`COleDataObject::GetData`|

Zazwyczaj średnika zostanie określona wraz z jego formatem Schowka. Na przykład obiekt **CF_EMBEDDEDSTRUCT** jest zawsze w `IStorage` średnim, który wymaga struktury **STGMEDIUM** . Z tego względu należy użyć, `GetData` ponieważ jest to jedyna z tych funkcji, które mogą akceptować strukturę **STGMEDIUM** .

W przypadku, gdy format schowka ma wartość `IStream` lub `HGLOBAL` średnią, struktura może dostarczyć `CFile` wskaźnik odwołujący się do danych. Aplikacja może następnie użyć odczytu pliku do uzyskania danych w taki sam sposób, w jaki może importować dane z pliku. Zasadniczo jest to interfejs po stronie klienta do `OnRenderData` `OnRenderFileData` procedur i w źródle danych.

Użytkownik może teraz wstawiać dane do dokumentu tak samo jak w przypadku innych danych w tym samym formacie.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Przeciągnij i upuść](drag-and-drop-ole.md)

- [Schowek](clipboard.md)

## <a name="see-also"></a>Zobacz też

[Obiekty danych i źródła danych (OLE)](data-objects-and-data-sources-ole.md)<br/>
[Klasa COleDataObject](reference/coledataobject-class.md)<br/>
[Klasa COleDataSource](reference/coledatasource-class.md)
