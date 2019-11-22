---
title: Klasy DAO
ms.date: 09/17/2019
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: cdd3fd9a733df73d36441693d049724878219df5
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303391"
---
# <a name="dao-classes"></a>Klasy DAO

Obiekty DAO są używane z bazami danych programu Access i są obsługiwane za pomocą pakietu Office 2013. Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały.

Te klasy współpracują z innymi klasami struktury aplikacji, aby zapewnić łatwy dostęp do baz danych obiektów dostępu do danych (DAO), które używają tego samego aparatu bazy danych co Microsoft Visual Basic i Microsoft Access. Klasy DAO mogą również uzyskiwać dostęp do wielu baz danych, dla których dostępne są sterowniki Open Database Connectivity (ODBC).

Programy korzystające z baz danych DAO będą mieć co najmniej obiekt `CDaoDatabase` i obiekt `CDaoRecordset`.

> [!NOTE]
>  Środowisko i C++ kreatory wizualne nie obsługują już obiektów DAO (chociaż klasy DAO są dołączone i nadal można ich używać). Firma Microsoft zaleca używanie ODBC w przypadku nowych projektów MFC. Obiektów DAO należy używać tylko w przypadku zarządzania istniejącymi aplikacjami.

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
Zarządza nazwaną, chronioną hasłem sesją bazy danych z logowania do wylogowania. Większość programów używa domyślnego obszaru roboczego.

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
Połączenie z bazą danych, za pomocą której można wykonywać operacje na danych.

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
Reprezentuje zestaw rekordów wybranych ze źródła danych.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Widok, w którym są wyświetlane rekordy bazy danych w kontrolkach.

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
Reprezentuje definicję zapytania, zazwyczaj zapisana w bazie danych.

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
Reprezentuje przechowywaną definicję tabeli bazowej lub dołączonej tabeli.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Reprezentuje warunek wyjątku wynikający z klas DAO.

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
Obsługuje procedury wymiany pól rekordów DAO (DFX) używane przez klasy bazy danych DAO. Zwykle nie używa się tej klasy.

## <a name="related-classes"></a>Powiązane klasy

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Hermetyzuje dojście do magazynu dla binarnego dużego obiektu (BLOB), takiego jak mapa bitowa. obiekty `CLongBinary` są używane do zarządzania dużymi obiektami danych przechowywanymi w tabelach bazy danych.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Otoka dla **waluty**typu automatyzacji OLE, typ arytmetyczny stałej z 15 cyfr przed separatorem dziesiętnym i 4 cyfr po.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Otoka **dla typu automatyzacji**OLE. Reprezentuje wartości daty i godziny.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Otoka **dla typu automatyzacji**OLE. Dane w **odmianie**s mogą być przechowywane w wielu formatach.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../mfc/class-library-overview.md)
