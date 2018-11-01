---
title: 'Kontenery: elementy klienckie'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
ms.openlocfilehash: e0d56d4a8f25828de954a78e9bafd8df150c7ff9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437014"
---
# <a name="containers-client-items"></a>Kontenery: elementy klienckie

W tym artykule opisano, co to są elementy klienckie i z klasy aplikacji powinien pochodzić elementy klienta.

Elementy klienckie są elementami danych należących do innej aplikacji, która są zawarte w albo odwołuje się dokument aplikacji kontenera OLE. Elementy klienckie, których dane są zawarte w dokumencie są osadzone; te, których dane są przechowywane w innej lokalizacji przywoływanej przez dokument kontenera są połączone.

Klasa dokumentu w aplikacji OLE pochodzi od klasy [COleDocument](../mfc/reference/coledocument-class.md) , a nie z `CDocument`. `COleDocument` Klasa dziedziczy `CDocument` wszystkie funkcje niezbędne do przy użyciu architektury dokument/widok na MFC, które aplikacje są oparte. `COleDocument` definiuje również interfejs, który traktuje dokumentu jako zbiór `CDocItem` obiektów. Kilka `COleDocument` funkcji elementów członkowskich są dostarczane na dodawanie, pobieranie i usuwanie elementów tej kolekcji.

Każda aplikacja kontenera powinien pochodzić z co najmniej jedną klasę z `COleClientItem`. Obiekty tej klasy reprezentują elementy, osadzony lub połączony w dokumencie OLE. Dla cyklu życia dokumentu zawierającego je, istnieją tych obiektów, chyba że zostaną one usunięte z dokumentu.

`CDocItem` jest klasą bazową dla `COleClientItem` i `COleServerItem`. Obiekty klasy pochodzące z tych dwóch pełnią rolę pośredników pomiędzy elementu OLE i aplikacje klienckie i serwerowe, odpowiednio. Każdym dodaniu nowego elementu OLE w dokumencie programu MFC framework dodaje nowy obiekt aplikację kliencką `COleClientItem`-klasy pochodnej do kolekcji dokument `CDocItem` obiektów.

## <a name="see-also"></a>Zobacz też

[Kontenery](../mfc/containers.md)<br/>
[Kontenery: pliki złożone](../mfc/containers-compound-files.md)<br/>
[Kontenery: kwestie dotyczące interfejsu użytkownika](../mfc/containers-user-interface-issues.md)<br/>
[Kontenery: funkcje zaawansowane](../mfc/containers-advanced-features.md)<br/>
[Klasa COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
[Klasa COleServerItem](../mfc/reference/coleserveritem-class.md)
