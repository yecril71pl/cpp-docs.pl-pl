---
title: 'Serwery: elementy serwera'
ms.date: 11/04/2016
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
ms.openlocfilehash: 8ae24104a30a0b44e92b889006907911124310f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355111"
---
# <a name="servers-server-items"></a>Serwery: elementy serwera

Gdy kontener uruchamia serwer, dzięki czemu użytkownik może edytować osadzony lub połączony element OLE, aplikacja serwera tworzy "element serwera". Element serwera, który jest obiektem klasy `COleServerItem`pochodnej , zapewnia interfejs między dokumentem serwera a aplikacją kontenera.

Klasa `COleServerItem` definiuje kilka zastępowalnych funkcji elementów członkowskich, które są wywoływane przez OLE, zwykle w odpowiedzi na żądania z kontenera. Elementy serwera mogą reprezentować część dokumentu serwera lub całego dokumentu. Gdy element OLE jest osadzony w dokumencie kontenera, element serwera reprezentuje cały dokument serwera. Gdy element OLE jest połączony, element serwera może reprezentować część dokumentu serwera lub całego dokumentu, w zależności od tego, czy łącze jest częścią, czy z całością.

W przykładzie [PROGRAMU HIERSVR,](../overview/visual-cpp-samples.md) na przykład `CServerItem`klasa elementu serwera, ma element członkowski, `CServerNode`który jest wskaźnikiem do obiektu klasy . Obiekt `CServerNode` jest węzłem w dokumencie aplikacji HIERSVR, który jest drzewem. Gdy `CServerNode` obiekt jest węzłem `CServerItem` głównym, obiekt reprezentuje cały dokument. Gdy `CServerNode` obiekt jest węzłem `CServerItem` podrzędnym, obiekt reprezentuje część dokumentu. Zobacz przykład MFC OLE [HIERSVR](../overview/visual-cpp-samples.md) na przykład tej interakcji.

## <a name="implementing-server-items"></a><a name="_core_implementing_server_items"></a>Implementowanie elementów serwera

Jeśli używasz kreatora aplikacji do tworzenia kodu "starter" dla aplikacji, wszystko, co musisz zrobić, aby uwzględnić elementy serwera w kodzie startowym, to wybrać jedną z opcji serwera ze strony Opcje OLE. W przypadku dodawania elementów serwera do istniejącej aplikacji wykonaj następujące czynności:

#### <a name="to-implement-a-server-item"></a>Aby zaimplementować element serwera

1. Wywodź `COleServerItem`klasę z pliku .

1. W klasie pochodnej należy zastąpić `OnDraw` funkcję elementu członkowskiego.

   Struktura wywołuje `OnDraw` renderowania elementu OLE do metapliku. Aplikacja kontenera używa tego metapliku do renderowania elementu. Klasa widoku aplikacji ma również `OnDraw` funkcję elementu członkowskiego, która jest używana do renderowania elementu, gdy aplikacja serwera jest aktywna.

1. Zaimplementuj `OnGetEmbeddedItem` zastąpienie dla klasy dokumentu serwera. Aby uzyskać więcej informacji, zobacz artykuł [Serwery: Implementowanie dokumentów serwera](../mfc/servers-implementing-server-documents.md) i przykładowy program MFC OLE [HIERSVR](../overview/visual-cpp-samples.md).

1. Zaimplementuj funkcję `OnGetExtent` członkowek klasy elementu serwera. Struktura wywołuje tę funkcję, aby pobrać rozmiar elementu. Domyślna implementacja nic nie robi.

## <a name="a-tip-for-server-item-architecture"></a><a name="_core_a_tip_for_server.2d.item_architecture"></a>Wskazówka dotycząca architektury elementu serwera

Jak wspomniano w [implementacji elementów serwera,](#_core_implementing_server_items)aplikacje serwera muszą być w stanie renderować elementy zarówno w widoku serwera, jak i w metapliku używanym przez aplikację kontenera. W architekturze aplikacji biblioteki klas programu Microsoft `OnDraw` Foundation funkcja elementu członkowskiego klasy widoku renderuje element podczas jego edycji (zobacz [CView::OnDraw](../mfc/reference/cview-class.md#ondraw) w *odwołaniu do biblioteki klas*). Element serwera `OnDraw` renderuje element do metapliku we wszystkich innych przypadkach (patrz [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)).

Można uniknąć powielania kodu, pisząc funkcje pomocnika w klasie dokumentu `OnDraw` serwera i wywołując je z funkcji w widoku i klas elementu serwera. MFC OLE próbki [HIERSVR](../overview/visual-cpp-samples.md) używa tej `CServerView::OnDraw` strategii: funkcje i `CServerItem::OnDraw` oba wywołać `CServerDoc::DrawTree` do renderowania elementu.

Widok i element mają `OnDraw` funkcje członkowskie, ponieważ są rysowane w różnych warunkach. Widok musi uwzględniać takie czynniki, jak powiększanie, rozmiar i zasięg zaznaczenia, przycinanie i elementy interfejsu użytkownika, takie jak paski przewijania. Element serwera, z drugiej strony, zawsze rysuje cały obiekt OLE.

Aby uzyskać więcej informacji, zobacz [CView::OnDraw](../mfc/reference/cview-class.md#ondraw), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw), i [COleServerDoc::OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) w *odwołaniu do biblioteki klas*.

## <a name="see-also"></a>Zobacz też

[Serwery](../mfc/servers.md)
