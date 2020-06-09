---
title: 'Kontenery: powiadomienia dotyczące elementów klienckich'
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
ms.openlocfilehash: 54b1b2a64685b00fb265e0f80c1f6ad878a7da85
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623014"
---
# <a name="containers-client-item-notifications"></a>Kontenery: powiadomienia dotyczące elementów klienckich

W tym artykule omówiono funkcje, które są wywoływane przez platformę MFC, gdy aplikacje serwera modyfikują elementy w dokumencie aplikacji klienckiej.

[COleClientItem](reference/coleclientitem-class.md) definiuje kilka funkcji, które są wywoływane w odpowiedzi na żądania z aplikacji składnika, która jest również nazywana aplikacją serwera. Te zastąpienia zwykle działają jako powiadomienia. Informują one o aplikacji kontenera różnych zdarzeń, takich jak przewijanie, aktywacja lub zmiana położenia, a także o zmianach wprowadzonych przez użytkownika podczas edytowania lub manipulowania elementami.

Struktura powiadamia aplikację kontenera o zmianach za pomocą wywołania do `COleClientItem::OnChange` , funkcji, której implementacja jest wymagana. Ta funkcja chroniona odbiera dwa argumenty. Pierwszy określa przyczynę zmiany elementu serwera:

|Powiadomienie|Znaczenie|
|------------------|-------------|
|**OLE_CHANGED**|Wygląd elementu OLE został zmieniony.|
|**OLE_SAVED**|Element OLE został zapisany.|
|**OLE_CLOSED**|Element OLE został zamknięty.|
|**OLE_RENAMED**|Zmieniono nazwę dokumentu serwera zawierającego element OLE.|
|**OLE_CHANGED_STATE**|Element OLE został zmieniony z jednego stanu na inny.|
|**OLE_CHANGED_ASPECT**|Aspekt rysowania elementu OLE został zmieniony przez strukturę.|

Te wartości pochodzą z wyliczenia **OLE_NOTIFICATION** , które jest zdefiniowane w Afxole. C.

Drugi argument tej funkcji określa, w jaki sposób element został zmieniony lub jaki stan został wprowadzony:

|Gdy pierwszy argument jest|Drugi argument|
|----------------------------|---------------------|
|**OLE_SAVED** lub **OLE_CLOSED**|Nie jest używany.|
|**OLE_CHANGED**|Określa aspekt elementu OLE, który został zmieniony.|
|**OLE_CHANGED_STATE**|Opisuje wprowadzony stan (*emptyState*, *loadedState*, *openState*, *activeState*lub *activeUIState*).|

Aby uzyskać więcej informacji o stanach, które może założyć element klienta, zobacz [kontenery: Stany elementów klienta](containers-client-item-states.md).

Struktura wywołuje, `COleClientItem::OnGetItemPosition` gdy element jest aktywowany do edycji w miejscu. Implementacja jest wymagana w przypadku aplikacji obsługujących edycję w miejscu. Kreator aplikacji MFC udostępnia podstawową implementację, która przypisuje współrzędne elementu do `CRect` obiektu, który jest przesyłany jako argument do `OnGetItemPosition` .

W przypadku zmiany położenia lub rozmiaru elementu OLE podczas edycji w miejscu należy zaktualizować informacje o położeniu elementu i prostokątach wycinków, a serwer musi odebrać informacje o zmianach. Platforma wywołuje `COleClientItem::OnChangeItemPosition` do tego celu. Kreator aplikacji MFC udostępnia przesłonięcie, które wywołuje funkcję klasy bazowej. Należy edytować funkcję, którą Kreator aplikacji zapisuje dla `COleClientItem` klasy pochodnej, tak aby funkcja aktualizuje wszystkie informacje przechowywane przez obiekt elementu klienta.

## <a name="see-also"></a>Zobacz też

[Containers](containers.md)<br/>
[Kontenery: stany elementu klienckiego](containers-client-item-states.md)<br/>
[COleClientItem:: OnChangeItemPosition](reference/coleclientitem-class.md#onchangeitemposition)
