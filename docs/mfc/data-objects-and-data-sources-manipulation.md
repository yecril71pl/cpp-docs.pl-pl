---
title: "Obiekty danych i źródła danych: manipulowanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4561e055bd258ba2b276075ff337d62cf194813b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="data-objects-and-data-sources-manipulation"></a>Obiekty danych i źródła danych: operowanie
Po utworzeniu obiektu danych lub źródła danych, można wykonywać wiele typowych operacji na danych, takich jak wstawianie i usuwanie danych wyliczania formatów, z których dane są, i inne. W tym artykule opisano niezbędne do zakończenia operacji najbardziej typowe techniki. Tematy obejmują:  
  
-   [Wstawianie danych do źródła danych](#_core_inserting_data_into_a_data_source)  
  
-   [Określanie dostępnych w obiekcie danych formatów](#_core_determining_the_formats_available_in_a_data_object)  
  
-   [Pobieranie danych z obiektu danych](#_core_retrieving_data_from_a_data_object)  
  
##  <a name="_core_inserting_data_into_a_data_source"></a>Wstawianie danych do źródła danych  
 Jak dane są wstawiane do źródła danych zależy od tego, czy dane są dostarczane bezpośrednio lub na żądanie, w których średnia podano. Dostępne są następujące możliwości.  
  
### <a name="supplying-data-immediately-immediate-rendering"></a>Dostarczająca dane od razu (renderowania bezpośrednim)  
  
-   Wywołanie `COleDataSource::CacheGlobalData` wielokrotnie dla każdego formatu Schowka, w którym są dostarczająca dane. Przekaż formatu schowka mają być używane, dojścia do pamięci zawierający dane i, opcjonalnie, **FORMATETC** struktury opisujący dane.  
  
     —lub—  
  
-   Jeśli chcesz pracować bezpośrednio z **STGMEDIUM** struktury, należy wywołać `COleDataSource::CacheData` zamiast `COleDataSource::CacheGlobalData` w powyższych opcji.  
  
### <a name="supplying-data-on-demand-delayed-rendering"></a>Udostępnia dane na żądanie (opóźnione renderowanie)  
 Jest to zaawansowane tematu.  
  
-   Wywołanie `COleDataSource::DelayRenderData` wielokrotnie dla każdego formatu Schowka, w którym są dostarczająca dane. Przekaż formatu Schowka do użycia i, opcjonalnie, **FORMATETC** struktury opisujący dane. Po zażądaniu danych platforma wywoła `COleDataSource::OnRenderData`, który należy zastąpić.  
  
     —lub—  
  
-   Jeśli używasz `CFile` obiektu jako źródło danych, wywołaj `COleDataSource::DelayRenderFileData` zamiast `COleDataSource::DelayRenderData` w poprzedniej opcji. Po zażądaniu danych platforma wywoła `COleDataSource::OnRenderFileData`, który należy zastąpić.  
  
##  <a name="_core_determining_the_formats_available_in_a_data_object"></a>Określanie dostępnych w obiekcie danych formatów  
 Zanim aplikacja umożliwia użytkownikowi wkleić dane, trzeba wiedzieć, czy istnieją formaty Schowka, który może obsługiwać. Aby to zrobić, aplikacja powinna wykonaj następujące czynności:  
  
1.  Utwórz `COleDataObject` obiektu i **FORMATETC** struktury.  
  
2.  Wywołanie obiektu danych `AttachClipboard` funkcji członkowskiej do skojarzenia obiektu danych z danych w Schowku.  
  
3.  Wykonaj jedną z następujących czynności:  
  
    -   Wywołanie obiektu danych `IsDataAvailable` funkcji członkowskiej, jeśli istnieje tylko jeden lub dwa formaty użytkownik należy. Spowoduje to zaoszczędzić czas w przypadkach, gdy dane w Schowku obsługuje znacznie więcej formatów niż aplikacja.  
  
         —lub—  
  
    -   Wywołanie obiektu danych `BeginEnumFormats` funkcji członkowskich rozpoczynają wyliczanie formatów dostępnych w Schowku. Następnie wywołaj `GetNextFormat` aż do Schowka zwraca obsługuje aplikację w formacie lub nie ma żadnych więcej formatów.  
  
 Jeśli używasz `ON_UPDATE_COMMAND_UI`, można teraz włączyć Wklej i prawdopodobnie Wklej specjalne elementy menu Edycja. W tym celu należy wywołać `CMenu::EnableMenuItem` lub `CCmdUI::Enable`. Aby uzyskać więcej informacji o jakie kontenera aplikacji powinien elementów menu i kiedy, zobacz [menu i zasoby: dodatki do kontenera](../mfc/menus-and-resources-container-additions.md).  
  
##  <a name="_core_retrieving_data_from_a_data_object"></a>Pobieranie danych z obiektu danych  
 Po podjęciu decyzji dotyczącej format danych, wszystkie te pozostaje jest pobrać dane z obiektu danych. Aby to zrobić, użytkownik decyduje o tym, gdzie umieścić dane, a aplikacja wymaga odpowiedniej funkcji. Dane będą dostępne w jednym z następujących nośników:  
  
|Średnia liczba godzin|Funkcji do wywołania|  
|------------|----------------------|  
|Pamięć globalna (`HGLOBAL`)|`COleDataObject::GetGlobalData`|  
|Plik (`CFile`)|`COleDataObject::GetFileData`|  
|**STGMEDIUM** struktury (`IStorage`)|`COleDataObject::GetData`|  
  
 Zazwyczaj nośnik zostanie określona wraz z jego formatu Schowka. Na przykład **CF_EMBEDDEDSTRUCT** obiektu jest zawsze w `IStorage` nośnika, który wymaga **STGMEDIUM** struktury. W związku z tym należy użyć `GetData` ponieważ jest tylko jeden z tych funkcji, które akceptują **STGMEDIUM** struktury.  
  
 W przypadku formatu Schowka w przypadkach `IStream` lub `HGLOBAL` średnia, zapewnia platformę `CFile` wskaźnika, który odwołuje się do danych. Aplikacja następnie można użyć pliku odczytać w celu uzyskania danych w taki sam sposób go może importować dane z pliku. Zasadniczo jest to interfejs klienta do `OnRenderData` i `OnRenderFileData` procedury w źródle danych.  
  
 Użytkownik może teraz wstawiania danych do dokumentu, podobnie jak w przypadku innych danych, w tym samym formacie.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Przeciągnij i upuść](../mfc/drag-and-drop-ole.md)  
  
-   [Schowka](../mfc/clipboard.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md)   
 [Klasa COleDataObject](../mfc/reference/coledataobject-class.md)   
 [COleDataSource — klasa](../mfc/reference/coledatasource-class.md)
