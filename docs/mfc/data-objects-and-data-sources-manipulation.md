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
ms.openlocfilehash: a08b6ff274c73d301c156d65aa56fbecca49128c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370549"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Obiekty danych i źródła danych: operowanie

Po utworzeniu obiektu danych lub źródła danych można wykonać wiele typowych operacji na danych, takich jak wstawianie i usuwanie danych, wyliczanie formatów, w których są dane i inne. W tym artykule opisano techniki niezbędne do wykonania najbardziej typowych operacji. Tematy obejmują:

- [Wstawianie danych do źródła danych](#_core_inserting_data_into_a_data_source)

- [Określanie formatów dostępnych w obiekcie danych](#_core_determining_the_formats_available_in_a_data_object)

- [Pobieranie danych z obiektu danych](#_core_retrieving_data_from_a_data_object)

## <a name="inserting-data-into-a-data-source"></a><a name="_core_inserting_data_into_a_data_source"></a>Wstawianie danych do źródła danych

Sposób wstawiania danych do źródła danych zależy od tego, czy dane są dostarczane natychmiast, czy na żądanie i na którym nośniku są dostarczane. Możliwości są następujące.

### <a name="supplying-data-immediately-immediate-rendering"></a>Natychmiastowe dostarczanie danych (natychmiastowe renderowanie)

- Wywołaj `COleDataSource::CacheGlobalData` wielokrotnie dla każdego formatu Schowka, w którym dostarczasz dane. Przekaż format Schowka do użycia, dojście do pamięci zawierającej dane i opcjonalnie strukturę **FORMATETC** opisującą dane.

     — lub —

- Jeśli chcesz pracować bezpośrednio ze strukturami **STGMEDIUM,** dzwonisz `COleDataSource::CacheData` zamiast w powyższej `COleDataSource::CacheGlobalData` opcji.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Dostarczanie danych na żądanie (opóźnione renderowanie)

Jest to zaawansowany temat.

- Wywołaj `COleDataSource::DelayRenderData` wielokrotnie dla każdego formatu Schowka, w którym dostarczasz dane. Przekaż format Schowka do użycia i opcjonalnie strukturę **FORMATETC** opisującą dane. Gdy dane są wymagane, struktura `COleDataSource::OnRenderData`wywoła , które należy zastąpić.

     — lub —

- Jeśli używasz `CFile` obiektu do poniesienia `COleDataSource::DelayRenderData` danych, wywołanie `COleDataSource::DelayRenderFileData` zamiast w poprzedniej opcji. Gdy dane są wymagane, struktura `COleDataSource::OnRenderFileData`wywoła , które należy zastąpić.

## <a name="determining-the-formats-available-in-a-data-object"></a><a name="_core_determining_the_formats_available_in_a_data_object"></a>Określanie formatów dostępnych w obiekcie danych

Zanim aplikacja pozwoli użytkownikowi wkleić do niego dane, musi wiedzieć, czy w Schowku znajdują się formaty, które może obsłużyć. Aby to zrobić, aplikacja powinna wykonać następujące czynności:

1. Utwórz `COleDataObject` obiekt i strukturę **FORMATETC.**

1. Wywołanie funkcji `AttachClipboard` elementu członkowskiego obiektu danych w celu skojarzenia obiektu danych z danymi w Schowku.

1. Wykonaj jedną z następujących czynności:

   - Wywołanie funkcji `IsDataAvailable` elementu członkowskiego obiektu danych, jeśli istnieje tylko jeden lub dwa formaty, które są potrzebne. Pozwoli to zaoszczędzić czas w przypadkach, gdy dane w Schowku obsługuje znacznie więcej formatów niż aplikacja.

     \-lub-

   - Wywołanie funkcji `BeginEnumFormats` elementu członkowskiego obiektu danych, aby rozpocząć wyliczanie formatów dostępnych w Schowku. Następnie `GetNextFormat` wywołaj, aż Schowek zwróci format, który obsługuje aplikacja lub nie ma więcej formatów.

Jeśli używasz **ON_UPDATE_COMMAND_UI,** możesz teraz włączyć wklej i ewentualnie wklej elementy specjalne w menu Edycja. Aby to zrobić, `CMenu::EnableMenuItem` zadzwoń `CCmdUI::Enable`albo lub . Aby uzyskać więcej informacji o tym, co aplikacje kontenerów powinny robić z elementami menu i kiedy, zobacz [Menu i zasoby: Dodatki kontenerów](../mfc/menus-and-resources-container-additions.md).

## <a name="retrieving-data-from-a-data-object"></a><a name="_core_retrieving_data_from_a_data_object"></a>Pobieranie danych z obiektu danych

Po podjęciu decyzji o formacie danych pozostaje tylko pobrać dane z obiektu danych. Aby to zrobić, użytkownik decyduje, gdzie umieścić dane, a aplikacja wywołuje odpowiednią funkcję. Dane będą dostępne w jednym z następujących nośników:

|Medium|Funkcja do wywołania|
|------------|----------------------|
|Pamięć globalna (`HGLOBAL`)|`COleDataObject::GetGlobalData`|
|Plik`CFile`( )|`COleDataObject::GetFileData`|
|**Struktura STGMEDIUM** (`IStorage`)|`COleDataObject::GetData`|

Powszechnie nośnik zostanie określony wraz z formatem Schowka. Na przykład **obiekt CF_EMBEDDEDSTRUCT** jest zawsze w `IStorage` medium, które wymaga struktury **STGMEDIUM.** W związku z `GetData` tym należy użyć, ponieważ jest to jedyna z tych funkcji, które mogą akceptować **STGMEDIUM** struktury.

W przypadkach, gdy format Schowka znajduje się `IStream` w lub `HGLOBAL` na nośniku, struktura może zapewnić `CFile` wskaźnik, który odwołuje się do danych. Aplikacja może następnie użyć odczytu pliku, aby uzyskać dane w taki sam sposób, jak może importować dane z pliku. Zasadniczo jest to interfejs po `OnRenderData` stronie `OnRenderFileData` klienta do i procedur w źródle danych.

Użytkownik może teraz wstawiać dane do dokumentu, tak jak w przypadku innych danych w tym samym formacie.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Przeciąganie i upuszczanie](../mfc/drag-and-drop-ole.md)

- [Schowek](../mfc/clipboard.md)

## <a name="see-also"></a>Zobacz też

[Obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[Klasa COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
[Klasa COleDataSource](../mfc/reference/coledatasource-class.md)
