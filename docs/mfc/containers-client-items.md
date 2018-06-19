---
title: 'Kontenery: Elementy klienckie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14979f1c5f11e9a229c408e33e7c17d8776a54a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344220"
---
# <a name="containers-client-items"></a>Kontenery: elementy klienckie
W tym artykule opisano, co to są elementy klienckie i z klasy co aplikacji powinien pochodzić jego elementy klienckie.  
  
 Elementy klienckie są elementy danych należących do innej aplikacji, które są zawarte w lub odwołuje się dokument aplikacji kontenera OLE. Elementy klienckie, których danych znajdujących się w dokumencie są osadzone; te, których dane są przechowywane w innej lokalizacji odwołuje się dokument kontenera są połączone.  
  
 Klasa dokumentu w aplikacji OLE pochodzi z klasy [COleDocument](../mfc/reference/coledocument-class.md) , a nie z **CDocument**. `COleDocument` Klasa dziedziczy **CDocument** wszystkie funkcje niezbędne do przy użyciu architektury dokument/widok, w którym MFC aplikacje są oparte. `COleDocument` definiuje również interfejs, który traktuje dokumentu jako kolekcja `CDocItem` obiektów. Kilka `COleDocument` funkcji elementów członkowskich są udostępniane dla Dodawanie, pobieranie i usuwanie elementów tej kolekcji.  
  
 Każda aplikacja kontenera powinien pochodzić z co najmniej jedną klasę z `COleClientItem`. Obiekty ta klasa reprezentuje elementy, osadzony czy połączony w dokumencie OLE. Te obiekty istnieje przez cały okres istnienia dokumentu zawierającego je, chyba że zostaną one usunięte z dokumentu.  
  
 `CDocItem` jest klasą bazową dla `COleClientItem` i `COleServerItem`. Obiektów klasy pochodzące z tych dwóch odpowiednio działać jako pośredników od elementu OLE i aplikacjom klienta i serwera. Każdym dodaniu nowego elementu OLE w dokumencie programu MFC framework dodaje nowy obiekt aplikacja kliencka `COleClientItem`-pochodnej klasy dokumentu kolekcji `CDocItem` obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery](../mfc/containers.md)   
 [Kontenery: Pliki złożone](../mfc/containers-compound-files.md)   
 [Kontenery: Problemy z interfejsem użytkownika](../mfc/containers-user-interface-issues.md)   
 [Kontenery: Funkcje zaawansowane](../mfc/containers-advanced-features.md)   
 [Klasa COleClientItem](../mfc/reference/coleclientitem-class.md)   
 [Klasa COleServerItem](../mfc/reference/coleserveritem-class.md)
