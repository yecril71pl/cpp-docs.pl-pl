---
title: "ODBC — klasy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.data
dev_langs: C++
helpviewer_keywords:
- database classes [MFC], ODBC
- ODBC classes [MFC]
ms.assetid: 6c40fca8-3033-4873-9abe-7f51725de0e0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 33fcc3453d36a2567330f60cec73383f842210c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="odbc-classes"></a>Klasy ODBC
Te klasy współpracować z innych aplikacji framework klas aby zapewnić łatwy dostęp do różnych baz danych, dla których dostępne są sterowniki otwarte połączenie bazy danych (ODBC).  
  
 Programy używające baz danych ODBC będzie miał co najmniej `CDatabase` obiektu i `CRecordset` obiektu.  
  
 [Cdatabase —](../mfc/reference/cdatabase-class.md)  
 Hermetyzuje połączenie ze źródłem danych, za pomocą których można korzystać w źródle danych.  
  
 [Crecordset —](../mfc/reference/crecordset-class.md)  
 Hermetyzuje zestawu rekordów wybrane źródła danych. Zestawy rekordów Włącz przewijania z rekordami, aktualizowania rekordów (Dodawanie, edytowanie i usuwanie rekordów), kwalifikujących się zaznaczenie z filtrem, sortowanie zaznaczenie, a Ustawianie wybór informacje uzyskane lub obliczane w czasie wykonywania.  
  
 [CRecordView](../mfc/reference/crecordview-class.md)  
 Formularz zawiera widok podłączone bezpośrednio do obiektu zestawu rekordów. (DDX) mechanizm wymiany danych między zestawu rekordów i kontrolki widoku rekordu wymiany danych okna dialogowego. Podobnie jak wszystkie widoki formularzy widoku rekordu zależy od zasobu szablonu okna dialogowego. Widoków rekordów również obsługuje przenoszenie z rekordami w zestawie rekordów, aktualizowanie rekordów i zamykania skojarzonych rekordów po zamknięciu widoku rekordu.  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 Wyjątek podczas przetwarzania wynikające z błędami dostępu do danych. Ta klasa obsługuje tę samą funkcję co inne klasy wyjątków w mechanizm obsługi wyjątków, biblioteki klas.  
  
 [CFieldExchange](../mfc/reference/cfieldexchange-class.md)  
 Udostępnia informacje o kontekście do obsługi wymiana pól rekordów (RFX), który wymienia dane między elementy członkowskie danych pola i elementy członkowskie danych parametru obiektu zestawu rekordów i na odpowiednie kolumny tabeli w źródle danych. Analogiczny do klasy [cdataexchange —](../mfc/reference/cdataexchange-class.md), podobnie używany dla wymiana danych okna dialogowego (DDX).  
  
## <a name="related-classes"></a>Klasy pokrewne  
 [Clongbinary —](../mfc/reference/clongbinary-class.md)  
 Hermetyzuje dojścia do magazynu dla dużego obiektu binarnego (BLOB), takich jak mapy bitowej. `CLongBinary`obiekty służą do zarządzania obiektami dużej ilości danych przechowywanych w tabelach bazy danych.  
  
 [Cdbvariant —](../mfc/reference/cdbvariant-class.md)  
 Służy do przechowywania wartości, nie martwiąc się o typ danych wartości. `CDBVariant`śledzi bieżącą wartość, który jest przechowywany w Unii typ danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

