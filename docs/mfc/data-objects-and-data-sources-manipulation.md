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
ms.openlocfilehash: adbe2a77fb0069e9874ab20a51b3ab08aabbe1f6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447003"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Obiekty danych i źródła danych: operowanie

Po utworzeniu obiektu danych lub źródła danych można wykonać kilka typowych operacji na danych, takich jak wstawianie i usuwanie danych, wyliczanie formatów, w których znajdują się dane, i inne. W tym artykule opisano techniki niezbędne do wykonania najbardziej typowych operacji. Tematy obejmują:

- [Wstawianie danych do źródła danych](#_core_inserting_data_into_a_data_source)

- [Określanie formatów dostępnych w obiekcie danych](#_core_determining_the_formats_available_in_a_data_object)

- [Pobieranie danych z obiektu danych](#_core_retrieving_data_from_a_data_object)

##  <a name="_core_inserting_data_into_a_data_source"></a>Wstawianie danych do źródła danych

Sposób wstawiania danych do źródła danych zależy od tego, czy dane są dostarczane bezpośrednio, czy na żądanie, i w którym dostarczanym nośniku. Te możliwości są następujące.

### <a name="supplying-data-immediately-immediate-rendering"></a>Dostarczanie danych natychmiast (bezpośrednie renderowanie)

- Wywołaj `COleDataSource::CacheGlobalData` wielokrotnie dla każdego formatu Schowka, w którym dane są dostarczane. Przekaż format schowka, który ma być używany, dojście do pamięci zawierającej dane i, opcjonalnie, strukturę **FORMATETC** opisującą dane.

     — lub —

- Jeśli chcesz bezpośrednio współpracować ze strukturami **STGMEDIUM** , możesz wywołać `COleDataSource::CacheData` zamiast `COleDataSource::CacheGlobalData` w powyższej opcji.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Dostarczanie danych na żądanie (opóźnione renderowanie)

To jest zaawansowany temat.

- Wywołaj `COleDataSource::DelayRenderData` wielokrotnie dla każdego formatu Schowka, w którym dane są dostarczane. Przekaż format schowka, aby można było go używać i opcjonalnie **FORMATETC** strukturę opisującą dane. Gdy dane są żądane, struktura wywoła `COleDataSource::OnRenderData`, które należy przesłonić.

     — lub —

- Jeśli używasz obiektu `CFile` do dostarczania danych, wywołaj `COleDataSource::DelayRenderFileData` zamiast `COleDataSource::DelayRenderData` w poprzedniej opcji. Gdy dane są żądane, struktura wywoła `COleDataSource::OnRenderFileData`, które należy przesłonić.

##  <a name="_core_determining_the_formats_available_in_a_data_object"></a>Określanie formatów dostępnych w obiekcie danych

Aby użytkownik mógł wkleić do niego dane, musi wiedzieć, czy w schowku znajdują się formaty, które może obsłużyć. W tym celu aplikacja powinna wykonać następujące czynności:

1. Utwórz obiekt `COleDataObject` i strukturę **FORMATETC** .

1. Wywołaj funkcję członkowską `AttachClipboard` obiektu danych, aby skojarzyć obiekt danych z danymi w Schowku.

1. Wykonaj jedną z następujących czynności:

   - Wywołaj funkcję członkowską `IsDataAvailable` obiektu danych, jeśli istnieje tylko jeden lub dwa formaty, które są potrzebne. Pozwoli to zaoszczędzić czas w przypadkach, gdy dane w schowku obsługują znacznie więcej formatów niż aplikacja.

     \-lub-

   - Wywołaj funkcję członkowską `BeginEnumFormats` obiektu danych, aby rozpocząć wyliczanie formatów dostępnych w Schowku. Następnie Wywołaj `GetNextFormat`, dopóki Schowek nie zwróci formatu obsługiwanego przez aplikację lub nie ma więcej formatów.

Jeśli używasz **ON_UPDATE_COMMAND_UI**, możesz teraz włączyć opcję Wklej i, ewentualnie Wklej elementy specjalne w menu Edycja. W tym celu wywołaj polecenie `CMenu::EnableMenuItem` lub `CCmdUI::Enable`. Aby uzyskać więcej informacji na temat aplikacji kontenera, które powinny być wykonywane z elementami menu i, zobacz [menu i zasoby: Dodatki do kontenera](../mfc/menus-and-resources-container-additions.md).

##  <a name="_core_retrieving_data_from_a_data_object"></a>Pobieranie danych z obiektu danych

Gdy użytkownik zdecyduje się na format danych, wszystko to, co pozostanie na pobranie danych z obiektu danych. W tym celu użytkownik decyduje, gdzie umieścić dane, a aplikacja wywołuje odpowiednią funkcję. Dane będą dostępne w jednym z następujących nośników:

|Medium|Funkcja do wywołania|
|------------|----------------------|
|Pamięć globalna (`HGLOBAL`)|`COleDataObject::GetGlobalData`|
|Plik (`CFile`)|`COleDataObject::GetFileData`|
|Struktura **STGMEDIUM** (`IStorage`)|`COleDataObject::GetData`|

Zazwyczaj średnika zostanie określona wraz z jego formatem Schowka. Na przykład obiekt **CF_EMBEDDEDSTRUCT** jest zawsze w `IStorage` medium, który wymaga struktury **STGMEDIUM** . W związku z tym należy używać `GetData`, ponieważ jest to jedyna z tych funkcji, które mogą akceptować strukturę **STGMEDIUM** .

W przypadku, gdy format schowka znajduje się w `IStream` lub `HGLOBAL` medium, struktura może zapewnić `CFile`y wskaźnik, który odwołuje się do danych. Aplikacja może następnie użyć odczytu pliku do uzyskania danych w taki sam sposób, w jaki może importować dane z pliku. Zasadniczo jest to interfejs po stronie klienta do `OnRenderData` i `OnRenderFileData` procedur w źródle danych.

Użytkownik może teraz wstawiać dane do dokumentu tak samo jak w przypadku innych danych w tym samym formacie.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Przeciągnij i upuść](../mfc/drag-and-drop-ole.md)

- [Schowek](../mfc/clipboard.md)

## <a name="see-also"></a>Zobacz też

[Obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[Klasa COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
[Klasa COleDataSource](../mfc/reference/coledatasource-class.md)
