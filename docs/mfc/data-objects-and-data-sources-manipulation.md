---
title: 'Obiekty danych i źródeł danych: manipulowanie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a5b44dd343c068a6a98765f9740dcd96b68bd323
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415498"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Obiekty danych i źródła danych: operowanie

Po utworzeniu obiektu danych lub źródła danych można wykonywać wiele typowych operacji na danych, takich jak wstawianie i usuwanie danych, wyliczanie formaty, w której znajduje się dane, i nie tylko. W tym artykule opisano techniki konieczny do realizacji typowych operacji. Tematy obejmują:

- [Wstawianie danych do źródła danych](#_core_inserting_data_into_a_data_source)

- [Określanie formatów dostępnych w obiekcie danych](#_core_determining_the_formats_available_in_a_data_object)

- [Pobieranie danych z obiektu danych](#_core_retrieving_data_from_a_data_object)

##  <a name="_core_inserting_data_into_a_data_source"></a> Wstawianie danych do źródła danych

Jak dane są wstawiane do źródła danych zależy od tego, czy dane są dostarczane bezpośrednio lub na żądanie, w których średnia jest dostarczany. Dostępne są następujące możliwości.

### <a name="supplying-data-immediately-immediate-rendering"></a>Dostarczanie danych natychmiast (renderowania bezpośrednim)

- Wywołaj `COleDataSource::CacheGlobalData` wielokrotnie dla każdego format Schowka, w którym są dostarczająca dane. Przekaż format Schowka, który ma być używany, dojścia do pamięci zawierający dane i, opcjonalnie, **FORMATETC** struktury opisujący dane.

     —lub—

- Jeśli chcesz współpracować bezpośrednio z **STGMEDIUM** struktury, należy wywołać `COleDataSource::CacheData` zamiast `COleDataSource::CacheGlobalData` w powyższych opcji.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Dostarczanie danych na żądanie (opóźnione renderowanie)

Jest to zaawansowane tematu.

- Wywołaj `COleDataSource::DelayRenderData` wielokrotnie dla każdego format Schowka, w którym są dostarczająca dane. Format Schowka, który ma być używany do przekazywania i, opcjonalnie, **FORMATETC** struktury opisujący dane. Jeśli wymagane są dane, struktura wywoła `COleDataSource::OnRenderData`, który należy zastąpić.

     —lub—

- Jeśli używasz `CFile` obiektu do dostarczania danych, wywołaj `COleDataSource::DelayRenderFileData` zamiast `COleDataSource::DelayRenderData` w przypadku poprzedniej opcji. Jeśli wymagane są dane, struktura wywoła `COleDataSource::OnRenderFileData`, który należy zastąpić.

##  <a name="_core_determining_the_formats_available_in_a_data_object"></a> Określanie formatów dostępnych w obiekcie danych

Zanim aplikacja umożliwia użytkownikowi wkleić dane, trzeba wiedzieć, czy formaty Schowka, która może obsłużyć. Aby to zrobić, aplikacja powinna wykonaj następujące czynności:

1. Tworzenie `COleDataObject` obiektu i **FORMATETC** struktury.

1. Wywołanie obiektu danych `AttachClipboard` funkcja elementu członkowskiego, aby skojarzyć obiekt danych przy użyciu danych w Schowku.

1. Wykonaj jedną z następujących czynności:

   - Wywołanie obiektu danych `IsDataAvailable` funkcja elementu członkowskiego, jeśli istnieje tylko jeden lub dwa formaty, użytkownik musi. Pozwoli to zaoszczędzić czas w przypadkach, w których dane w Schowku obsługuje formaty znacznie więcej niż aplikacja.

         -or-

   - Wywołanie obiektu danych `BeginEnumFormats` funkcja elementu członkowskiego rozpoczynają wyliczanie formatów dostępnych w Schowku. Następnie wywołaj `GetNextFormat` aż do momentu powrotu Schowka formatu aplikacja obsługuje lub jest nie więcej formatów.

Jeśli używasz **ON_UPDATE_COMMAND_UI**, można teraz włączyć Wklej i prawdopodobnie Wklej specjalne elementy menu Edycja. W tym celu należy wywołać `CMenu::EnableMenuItem` lub `CCmdUI::Enable`. Aby uzyskać więcej informacji o jakie kontenera aplikacji należy zrobić z elementami menu i when, zobacz [menu i zasoby: dodatki do kontenera](../mfc/menus-and-resources-container-additions.md).

##  <a name="_core_retrieving_data_from_a_data_object"></a> Pobieranie danych z obiektu danych

Gdy zdecydujesz się na format danych, pozostaje tylko do pobierania danych z obiektu danych. Aby to zrobić, użytkownik decyduje, gdzie umieścić dane, a aplikacja wywołuje odpowiednią funkcję. Dane będą dostępne w jednym z następujących nośników:

|Średni|Funkcja do wywołania|
|------------|----------------------|
|Pamięć globalna (`HGLOBAL`)|`COleDataObject::GetGlobalData`|
|Plik (`CFile`)|`COleDataObject::GetFileData`|
|**STGMEDIUM** struktury (`IStorage`)|`COleDataObject::GetData`|

Często nośnik zostanie określony, wraz z jego format Schowka. Na przykład **CF_EMBEDDEDSTRUCT** obiekt zawsze znajduje się w `IStorage` nośnika, który wymaga **STGMEDIUM** struktury. W związku z tym, należy użyć `GetData` ponieważ jest tylko jeden z tych funkcji, które mogą akceptować **STGMEDIUM** struktury.

W przypadkach, gdzie jest format Schowka w `IStream` lub `HGLOBAL` średni, struktura może zapewnić `CFile` wskaźnika, który odwołuje się do danych. Aplikacja może następnie używać pliku odczytać w celu uzyskania danych w taki sam sposób go może importować dane z pliku. Zasadniczo jest to interfejs klienta do `OnRenderData` i `OnRenderFileData` procedur w źródle danych.

Użytkownik może teraz wstawiania danych do dokumentu, podobnie jak w przypadku innych danych, w tym samym formacie.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Przeciąganie i upuszczanie](../mfc/drag-and-drop-ole.md)

- [Schowek](../mfc/clipboard.md)

## <a name="see-also"></a>Zobacz też

[Obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[Klasa COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
[Klasa COleDataSource](../mfc/reference/coledatasource-class.md)
