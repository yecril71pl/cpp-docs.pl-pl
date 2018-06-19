---
title: 'Kontenery: Powiadomienia dotyczące elementów klienckich | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2255f28c1250096bfbeb1a9365c57f78e17e20d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344627"
---
# <a name="containers-client-item-notifications"></a>Kontenery: powiadomienia dotyczące elementów klienckich
W tym artykule omówiono funkcje możliwym do zastąpienia, które programu MFC framework wymaga aplikacji serwerowych modyfikowania elementów w dokumencie aplikacji klienta.  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md) definiuje kilka funkcji możliwym do zastąpienia, które są wywoływane w odpowiedzi na żądania z zastosowania składnika, który jest również nazywany aplikacji serwera. Te z możliwością zastąpienia zazwyczaj działają jako powiadomienia. Informują aplikacji kontenera różnych zdarzeń, takich jak aktywacja przewijania, lub zmień położenie i zmiany, które użytkownik wprowadza podczas edytowania lub innego manipulowania elementu.  
  
 Platformę powiadamia zmian za pomocą wywołania do aplikacji kontenera `COleClientItem::OnChange`, funkcja możliwym do zastąpienia, którego implementacja jest wymagana. Ta funkcja chronionych otrzymuje dwa argumenty. Pierwszy określa przyczynę serwera zmienione elementu:  
  
|powiadomienia|Znaczenie|  
|------------------|-------------|  
|`OLE_CHANGED`|Wygląd elementu OLE została zmieniona.|  
|`OLE_SAVED`|Element OLE został zapisany.|  
|`OLE_CLOSED`|Element OLE został zamknięty.|  
|**OLE_RENAMED**|Zmieniono nazwę dokumentu zawierającego element OLE na serwerze.|  
|`OLE_CHANGED_STATE`|Element OLE zmienił się z jednego stanu do innego.|  
|**OLE_CHANGED_ASPECT**|Aspekt rysowania elementu OLE został zmieniony przez platformę.|  
  
 Te wartości są z **OLE_NOTIFICATION** wyliczenia, która jest zdefiniowana w AFXOLE. H.  
  
 Drugi argument do funkcji określa, jak element został zmieniony lub co stanie się, że ma pojawił się:  
  
|Gdy jest pierwszym argumentem|Drugi argument|  
|----------------------------|---------------------|  
|`OLE_SAVED` lub `OLE_CLOSED`|Nie jest używany.|  
|`OLE_CHANGED`|Określa aspekt elementu OLE, który został zmieniony.|  
|`OLE_CHANGED_STATE`|Opis stanu wprowadzane (`emptyState`, **loadedState**, `openState`, `activeState`, lub `activeUIState`).|  
  
 Aby uzyskać więcej informacji na temat stanów elementu klienta można założyć, zobacz [kontenery: stany elementu klienckiego](../mfc/containers-client-item-states.md).  
  
 Wywołania framework `COleClientItem::OnGetItemPosition` gdy element jest aktywowany do edycji w miejscu. Implementacja jest wymagany dla aplikacji, które obsługują edycji w miejscu. Kreator aplikacji MFC udostępnia podstawową implementację, który przypisuje do elementu współrzędnych w celu `CRect` obiekt, który jest przekazywany jako argument `OnGetItemPosition`.  
  
 Zmiana położenia lub rozmiar elementu OLE podczas edycji w miejscu, muszą zostać zaktualizowane kontenera informacji na temat pozycji i prostokąty wycinka elementu, a serwer musi odebrać informacje o zmianach. Wywołania framework `COleClientItem::OnChangeItemPosition` w tym celu. Kreator aplikacji MFC zawiera zastąpienia, która wywołuje funkcję klasy podstawowej. Należy edytować funkcji, która zapisuje Kreatora aplikacji dla programu `COleClientItem`-pochodnej klasy tak, aby funkcja aktualizuje wszystkie informacje przechowywane przez obiekt elementu klienta.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery](../mfc/containers.md)   
 [Kontenery: Stany elementu klienckiego](../mfc/containers-client-item-states.md)   
 [COleClientItem::OnChangeItemPosition](../mfc/reference/coleclientitem-class.md#onchangeitemposition)

