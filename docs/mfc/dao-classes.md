---
title: Klasy DAO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f43595ca5f688372a70999231ceebec5282cd3b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dao-classes"></a>Klasy DAO
Te klasy współpracować z innych aplikacji framework klas aby zapewnić łatwy dostęp do baz danych obiektu DAO (Data Access), korzystających z tego samego aparatu bazy danych programu Microsoft Visual Basic i programu Microsoft Access. Klasy DAO można także uzyskać dostęp do różnych baz danych, dla których dostępne są sterowniki otwarte połączenie bazy danych (ODBC).  
  
 Programy, które używają bazy danych DAO będzie miał co najmniej `CDaoDatabase` obiektu i `CDaoRecordset` obiektu.  
  
> [!NOTE]
>  Środowiska Visual C++ i kreatorów już obsługiwać DAO (mimo że uwzględniono klasy DAO i nadal można ich używać). Firma Microsoft zaleca używanie ODBC dla nowych projektów MFC. Obiekty DAO należy używać tylko w zachowaniu istniejących aplikacji.  
  
 [CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)  
 Zarządza sesji bazy danych o nazwie, chroniony hasłem z logowania do wylogowania. Większość programów używa domyślny obszar roboczy.  
  
 [CDaoDatabase](../mfc/reference/cdaodatabase-class.md)  
 Połączenie z bazą danych za pomocą których może wykonywać operacje na danych.  
  
 [Cdaorecordset —](../mfc/reference/cdaorecordset-class.md)  
 Reprezentuje zestaw rekordów wybrane źródła danych.  
  
 [CDaoRecordView](../mfc/reference/cdaorecordview-class.md)  
 Widok, który wyświetla rekordów bazy danych w kontrolkach.  
  
 [CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)  
 Reprezentuje definicji zapytania, zazwyczaj jest to jeden zapisane w bazie danych.  
  
 [CDaoTableDef](../mfc/reference/cdaotabledef-class.md)  
 Reprezentuje przechowywanych definicji tabeli podstawowej lub dołączonej tabeli.  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 Reprezentuje warunku wyjątku wynikających z klasy DAO.  
  
 [CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)  
 Obsługuje procedury programu exchange (DFX) pól rekordów DAO używane przez klas baz danych DAO. Zwykle nie użyje bezpośrednio do tej klasy.  
  
## <a name="related-classes"></a>Klasy pokrewne  
 [Clongbinary —](../mfc/reference/clongbinary-class.md)  
 Hermetyzuje dojścia do magazynu dla dużego obiektu binarnego (BLOB), takich jak mapy bitowej. `CLongBinary` obiekty służą do zarządzania obiektami dużej ilości danych przechowywanych w tabelach bazy danych.  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 Otoki dla typu automatyzacji OLE **waluty**, stałoprzecinkowe typ arytmetyczny, 4 cyfry po i przed separatorem dziesiętnym do 15 cyfr.  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 Otoki dla typu automatyzacji OLE **data**. Reprezentuje wartości daty i godziny.  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 Otoki dla typu automatyzacji OLE **VARIANT**. Dane w **VARIANT**s mogą być przechowywane w wielu formatach.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

