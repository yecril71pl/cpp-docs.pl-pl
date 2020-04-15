---
title: Klasy DAO
ms.date: 09/17/2019
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 7ae85cbeb7790cadb8c26dfbdb7a5163dbcd47c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373516"
---
# <a name="dao-classes"></a>Klasy DAO

DAO jest używany z bazami danych programu Access i jest obsługiwany przez pakiet Office 2013. DAO 3.6 jest ostateczną wersją i jest uważana za przestarzałą.

Te klasy współpracują z innymi klasami struktury aplikacji, aby zapewnić łatwy dostęp do baz danych obiektów dostępu do danych (DAO), które używają tego samego aparatu bazy danych co programy Microsoft Visual Basic i Microsoft Access. Klasy DAO mogą również uzyskać dostęp do szerokiej gamy baz danych, dla których dostępne są sterowniki Open Database Connectivity (ODBC).

Programy korzystające z baz danych DAO `CDaoDatabase` będą `CDaoRecordset` miały co najmniej obiekt i obiekt.

> [!NOTE]
> Środowisko Visual C++ i kreatory nie obsługują już DAO (chociaż klasy DAO są uwzględniane i nadal można ich używać). Firma Microsoft zaleca używanie odbc dla nowych projektów MFC. Dao należy używać tylko w utrzymaniu istniejących aplikacji.

[Cdaoworkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
Zarządza nazwaną, chroniną hasłem sesją bazy danych od logowania do wylogowywania. Większość programów używa domyślnego obszaru roboczego.

[Cdaodatabase](../mfc/reference/cdaodatabase-class.md)<br/>
Połączenie z bazą danych, za pośrednictwem której można obsługiwać dane.

[Cdaorecordset](../mfc/reference/cdaorecordset-class.md)<br/>
Reprezentuje zestaw rekordów wybranych ze źródła danych.

[Cdaorecordview](../mfc/reference/cdaorecordview-class.md)<br/>
Widok, który wyświetla rekordy bazy danych w formantach.

[Cdaoquerydef](../mfc/reference/cdaoquerydef-class.md)<br/>
Reprezentuje definicję kwerendy, zwykle jeden zapisany w bazie danych.

[Cdaotabledef](../mfc/reference/cdaotabledef-class.md)<br/>
Reprezentuje przechowywaną definicję tabeli bazowej lub dołączonej tabeli.

[Cdaoexception](../mfc/reference/cdaoexception-class.md)<br/>
Reprezentuje warunek wyjątku wynikający z klas DAO.

[CDaoFieldExchange (CDaoFieldExchange)](../mfc/reference/cdaofieldexchange-class.md)<br/>
Obsługuje procedury wymiany pól rekordów DAO (DFX) używane przez klasy bazy danych DAO. Zwykle nie będzie bezpośrednio używać tej klasy.

## <a name="related-classes"></a>Powiązane klasy

[Clongbinary](../mfc/reference/clongbinary-class.md)<br/>
Hermetyzuje dojście do magazynu dla binarnego dużego obiektu (BLOB), takiego jak mapa bitowa. `CLongBinary`obiekty są używane do zarządzania dużymi obiektami danych przechowywanymi w tabelach bazy danych.

[Colecurrency](../mfc/reference/colecurrency-class.md)<br/>
Otoka dla typu automatyzacji OLE **CURRENCY**, typu arytmetycznego o stałym punkcie, z 15 cyframi przed przecinkiem dziesiętnym i 4 cyframi po.

[Coledatetime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Otoka dla typu automatyzacji OLE **DATE**. Reprezentuje wartości daty i godziny.

[Colevariant](../mfc/reference/colevariant-class.md)<br/>
Otoka dla typu automatyzacji OLE **VARIANT**. Dane w **VARIANT**S mogą być przechowywane w wielu formatach.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
