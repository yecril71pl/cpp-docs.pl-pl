---
title: 'Serwery: Elementy serwera'
ms.date: 11/04/2016
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
ms.openlocfilehash: 0adaea1c4f1dd0525ead82dfffdf267326ac865c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262288"
---
# <a name="servers-server-items"></a>Serwery: Elementy serwera

Gdy kontener uruchamia serwer, dzięki czemu użytkownik może edytować element osadzony lub połączony OLE, aplikacja serwera tworzy "pozycja serwera". Element serwera, który jest obiektem klasy pochodne `COleServerItem`, udostępnia interfejs między dokument serwera i aplikacji kontenera.

`COleServerItem` Klasa definiuje kilka funkcji Członkowskich możliwym do zastąpienia, które są wywoływane przez OLE, zwykle w odpowiedzi na żądania z kontenera. Elementy serwera może reprezentować części dokumentu na serwerze lub całego dokumentu. Osadzone elementu OLE w dokumencie kontenera elementu serwera reprezentuje dokumentu całego serwera. Po połączeniu elementu OLE element serwera może reprezentować części dokumentu na serwerze lub całego dokumentu w zależności od tego, czy łącze do części lub całości.

W [HIERSVR](../visual-cpp-samples.md) przykładowy, na przykład klasa element serwera `CServerItem`, ma elementu członkowskiego, który jest wskaźnikiem do obiektu klasy `CServerNode`. `CServerNode` Obiektu jest węzłem w dokumencie aplikacji HIERSVR, w którym jest drzewo. Gdy `CServerNode` obiekt jest węzeł główny `CServerItem` obiekt reprezentuje cały dokument. Gdy `CServerNode` obiektu jest elementem podrzędnym, `CServerItem` obiekt reprezentuje część dokumentu. Zobacz przykładową MFC OLE [HIERSVR](../visual-cpp-samples.md) przykład interakcji.

##  <a name="_core_implementing_server_items"></a> Implementowanie elementy serwera

Użyj Kreatora aplikacji, aby utworzyć "starter" kod aplikacji, co należy zrobić, aby uwzględnić elementy serwera w kodzie modułu uruchamiającego jest wybierz jedną z opcji serwer ze strony opcje OLE. W przypadku dodawania serwera elementy do istniejącej aplikacji, wykonaj następujące czynności:

#### <a name="to-implement-a-server-item"></a>Aby zaimplementować element serwera

1. Wyprowadzić klasę z `COleServerItem`.

1. W klasie pochodnej, należy zastąpić `OnDraw` funkcja elementu członkowskiego.

   Struktura wywołuje `OnDraw` aby renderować element OLE w metaplik. Aplikacja kontenera używa tego metaplik do renderowania elementu. Klasa widoku aplikacji ma również `OnDraw` funkcja elementu członkowskiego, który jest używany do renderowania elementu, gdy aplikacja serwera jest aktywny.

1. Implementowanie nadpisanie `OnGetEmbeddedItem` dla swojej klasy dokumentu na serwerze. Aby uzyskać więcej informacji, zobacz artykuł [serwerów: Implementowanie dokumentów serwera](../mfc/servers-implementing-server-documents.md) przykład MFC OLE i [HIERSVR](../visual-cpp-samples.md).

1. Implementowanie klasy elementu serwera `OnGetExtent` funkcja elementu członkowskiego. Struktura wywołuje tę funkcję, aby pobrać rozmiar elementu. Domyślna implementacja nic nie robi.

##  <a name="_core_a_tip_for_server.2d.item_architecture"></a> Wskazówka dla architektury serwera elementu

Jak wspomniano w [elementy serwera wdrażania](#_core_implementing_server_items), serwera aplikacji musi być w stanie do renderowania elementów zarówno w widoku do serwera, jak i w metaplik używanych przez aplikację kontenera. W bibliotekę Microsoft Foundation Class architektury aplikacji, widok klasy firmy `OnDraw` funkcja elementu członkowskiego powoduje wyświetlenie elementu, gdy jest edytowany (zobacz [CView::OnDraw](../mfc/reference/cview-class.md#ondraw) w *odwołanie do biblioteki klas* ). Element serwera `OnDraw` renderuje element w metaplik we wszystkich innych przypadkach (zobacz [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)).

Można uniknąć duplikowania kodu, pisanie funkcji pomocnika w klasie dokumentu na serwerze i wywołując je z `OnDraw` funkcje w Twoich zajęciach widoku i elementu serwera. Przykładowe MFC OLE [HIERSVR](../visual-cpp-samples.md) korzysta z tej strategii: funkcje `CServerView::OnDraw` i `CServerItem::OnDraw` oba wywołania `CServerDoc::DrawTree` do renderowania elementu.

Widoku i elementu `OnDraw` funkcje Członkowskie, ponieważ można narysować w różnych warunkach. Widok należy wziąć pod uwagę takie czynniki jak powiększania, rozmiar zaznaczenia i zakresu, wycinka i elementy interfejsu użytkownika, takie jak paski przewijania. Element serwera, z drugiej strony, zawsze rysuje całego obiektu OLE.

Aby uzyskać więcej informacji, zobacz [CView::OnDraw](../mfc/reference/cview-class.md#ondraw), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw), i [COleServerDoc::OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)w *klasy odwołanie do biblioteki*.

## <a name="see-also"></a>Zobacz także

[Serwery](../mfc/servers.md)
