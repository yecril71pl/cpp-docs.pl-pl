---
title: 'Kontenery: powiadomienia dotyczące elementów klienckich'
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
ms.openlocfilehash: b59ba84c27d9ed4c964bd308cf69f9f729eb3c39
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528898"
---
# <a name="containers-client-item-notifications"></a>Kontenery: powiadomienia dotyczące elementów klienckich

W tym artykule omówiono funkcje możliwym do zastąpienia, które wywołuje struktura MFC, gdy aplikacje serwera modyfikować elementów w dokumencie aplikację kliencką.

[COleClientItem](../mfc/reference/coleclientitem-class.md) definiuje kilka funkcji możliwym do zastąpienia, które są wywoływane w odpowiedzi na żądania z aplikacji składnika, który jest również nazywany aplikacji serwera. Te / / overridables zazwyczaj działa jako powiadomienia. Poinformuj ich aplikacji kontenera różnych zdarzeniami, na przykład przewijania, aktywacji lub zmiana położenia i zmiany, które użytkownik wprowadza podczas edytowania lub innego manipulowania elementu.

Struktura powiadamia aplikację kontenera zmian za pomocą wywołania `COleClientItem::OnChange`, funkcję możliwym do zastąpienia, którego implementacja jest wymagana. Ta funkcja chronionych otrzymuje dwa argumenty. Pierwszy określa przyczynę, że serwer zmieniony element:

|Powiadomienia|Znaczenie|
|------------------|-------------|
|**OLE_CHANGED**|Wygląd elementu OLE został zmieniony.|
|**OLE_SAVED**|Zapisano element OLE.|
|**OLE_CLOSED**|Element OLE został zamknięty.|
|**OLE_RENAMED**|Zmieniono nazwę dokumentu zawierającego element OLE na serwerze.|
|**OLE_CHANGED_STATE**|Element OLE zmienił się z jednego stanu do drugiego.|
|**OLE_CHANGED_ASPECT**|Aspekt rysowania elementu OLE został zmieniony przez platformę.|

Te wartości pochodzą z **OLE_NOTIFICATION** wyliczenia, która jest zdefiniowana w AFXOLE. H.

Drugi argument do tej funkcji określa, jak element został zmieniony lub co się stanie, że został wprowadzony:

|Jeśli pierwszy argument jest|Drugi argument funkcji|
|----------------------------|---------------------|
|**OLE_SAVED** lub **OLE_CLOSED**|Nie jest używana.|
|**OLE_CHANGED**|Określa aspekt elementu OLE, które uległy zmianie.|
|**OLE_CHANGED_STATE**|Opisuje stan wprowadzanych (*emptyState*, *loadedState*, *openState*, *activeState*, lub  *activeUIState*).|

Aby uzyskać więcej informacji na temat stanów elementu klienta, można założyć, zobacz [kontenery: stany elementu klienckiego](../mfc/containers-client-item-states.md).

Struktura wywołuje `COleClientItem::OnGetItemPosition` gdy element jest aktywowany do edycji w miejscu. Implementacja jest wymagana dla aplikacji, które obsługują edycję w miejscu. Kreator aplikacji MFC dostarcza podstawową implementację, który przypisuje współrzędne elementu do `CRect` obiektu, który jest przekazywany jako argument do `OnGetItemPosition`.

Jeśli położenie i rozmiar elementu OLE zmienia się podczas edycji w miejscu, muszą zostać zaktualizowane kontenera informacji na temat elementu położenie i prostokąty przycinania, a serwer musi odebrać informacje o zmianach. Struktura wywołuje `COleClientItem::OnChangeItemPosition` do tego celu. Kreator aplikacji MFC zawiera przesłonięcie, który wywołuje funkcję klasy bazowej. Należy edytować funkcji, która zapisuje Kreatora aplikacji, dla Twojego `COleClientItem`-klasy pochodnej, tak aby funkcja aktualizuje wszystkie informacje przechowywane przez obiekt elementu klienta.

## <a name="see-also"></a>Zobacz też

[Kontenery](../mfc/containers.md)<br/>
[Kontenery: stany elementu klienckiego](../mfc/containers-client-item-states.md)<br/>
[COleClientItem::OnChangeItemPosition](../mfc/reference/coleclientitem-class.md#onchangeitemposition)

