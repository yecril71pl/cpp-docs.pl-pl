---
title: Klasy DAO
ms.date: 09/17/2019
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 51abd29ef4de5d70f4a5b2b6b14b53510e7876a1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615934"
---
# <a name="dao-classes"></a>Klasy DAO

Obiekty DAO są używane z bazami danych programu Access i są obsługiwane za pomocą pakietu Office 2013. Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały.

Te klasy współpracują z innymi klasami struktury aplikacji, aby zapewnić łatwy dostęp do baz danych obiektów dostępu do danych (DAO), które używają tego samego aparatu bazy danych co Microsoft Visual Basic i Microsoft Access. Klasy DAO mogą również uzyskiwać dostęp do wielu baz danych, dla których dostępne są sterowniki Open Database Connectivity (ODBC).

Programy korzystające z baz danych DAO będą mieć co najmniej `CDaoDatabase` obiekt i `CDaoRecordset` obiekt.

> [!NOTE]
> Visual C++ środowisko i kreatory nie obsługują już obiektów DAO (chociaż klasy DAO są dołączone i nadal można z nich korzystać). Firma Microsoft zaleca używanie ODBC w przypadku nowych projektów MFC. Obiektów DAO należy używać tylko w przypadku zarządzania istniejącymi aplikacjami.

[CDaoWorkspace](reference/cdaoworkspace-class.md)<br/>
Zarządza nazwaną, chronioną hasłem sesją bazy danych z logowania do wylogowania. Większość programów używa domyślnego obszaru roboczego.

[CDaoDatabase](reference/cdaodatabase-class.md)<br/>
Połączenie z bazą danych, za pomocą której można wykonywać operacje na danych.

[CDaoRecordset](reference/cdaorecordset-class.md)<br/>
Reprezentuje zestaw rekordów wybranych ze źródła danych.

[CDaoRecordView](reference/cdaorecordview-class.md)<br/>
Widok, w którym są wyświetlane rekordy bazy danych w kontrolkach.

[CDaoQueryDef](reference/cdaoquerydef-class.md)<br/>
Reprezentuje definicję zapytania, zazwyczaj zapisana w bazie danych.

[CDaoTableDef](reference/cdaotabledef-class.md)<br/>
Reprezentuje przechowywaną definicję tabeli bazowej lub dołączonej tabeli.

[CDaoException](reference/cdaoexception-class.md)<br/>
Reprezentuje warunek wyjątku wynikający z klas DAO.

[CDaoFieldExchange](reference/cdaofieldexchange-class.md)<br/>
Obsługuje procedury wymiany pól rekordów DAO (DFX) używane przez klasy bazy danych DAO. Zwykle nie używa się tej klasy.

## <a name="related-classes"></a>Powiązane klasy

[CLongBinary](reference/clongbinary-class.md)<br/>
Hermetyzuje dojście do magazynu dla binarnego dużego obiektu (BLOB), takiego jak mapa bitowa. `CLongBinary`obiekty służą do zarządzania dużymi obiektami danych przechowywanymi w tabelach bazy danych.

[COleCurrency](reference/colecurrency-class.md)<br/>
Otoka dla **waluty**typu automatyzacji OLE, typ arytmetyczny stałej z 15 cyfr przed separatorem dziesiętnym i 4 cyfr po.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Otoka **dla typu automatyzacji**OLE. Reprezentuje wartości daty i godziny.

[COleVariant](reference/colevariant-class.md)<br/>
Otoka **dla typu automatyzacji**OLE. Dane w **odmianie**s mogą być przechowywane w wielu formatach.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
