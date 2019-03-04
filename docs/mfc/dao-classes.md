---
title: Klasy DAO
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- database classes [MFC], DAO
- DAO [MFC], classes
ms.assetid: b15d0cd6-328b-4288-9c19-d037a795db57
ms.openlocfilehash: 238aab0a1948f16a85b8ea16719b75b49f5e69c8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287495"
---
# <a name="dao-classes"></a>Klasy DAO

Te klasy działają z innych aplikacji framework klas w celu zapewnienia łatwego dostępu do baz danych Access obiekt DAO (Data), korzystających z tego samego aparatu bazy danych programu Microsoft Visual Basic oraz Microsoft Access. Klasy DAO mogą też uzyskiwać dostęp szerokiej gamy baz danych, dla których dostępne są sterowników Open Database Connectivity (ODBC).

Programy, które korzystają z baz danych DAO będzie mieć co najmniej jeden `CDaoDatabase` obiektu i `CDaoRecordset` obiektu.

> [!NOTE]
>  Środowiska Visual C++ i kreatory nie obsługują już DAO (mimo że uwzględniono klas DAO i nadal można użyć). Firma Microsoft zaleca używanie ODBC dla nowych projektów MFC. DAO należy używać tylko w zachowaniu istniejących aplikacji.

[CDaoWorkspace](../mfc/reference/cdaoworkspace-class.md)<br/>
Zarządza sesję o nazwie bazy danych chronionej hasłem z logowania do wylogowania. Większość programów używa domyślnego obszaru roboczego.

[CDaoDatabase](../mfc/reference/cdaodatabase-class.md)<br/>
Połączenie z bazą danych, dzięki któremu można działać na danych.

[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)<br/>
Reprezentuje zestaw rekordów wybranych ze źródła danych.

[CDaoRecordView](../mfc/reference/cdaorecordview-class.md)<br/>
Widok wyświetlający rekordy bazy danych w kontrolkach.

[CDaoQueryDef](../mfc/reference/cdaoquerydef-class.md)<br/>
Reprezentuje definicję kwerendy, zazwyczaj jedna zapisana w bazie danych.

[CDaoTableDef](../mfc/reference/cdaotabledef-class.md)<br/>
Przedstawia przechowywaną definicję tabeli bazowej lub dołączonej tabeli.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Przedstawia warunek wyjątku wynikający z klas DAO.

[CDaoFieldExchange](../mfc/reference/cdaofieldexchange-class.md)<br/>
Obsługuje procedury wymiany (DXF) pola rekordów DAO używanych przez klasy bazy danych DAO. Zwykle nie użyje bezpośrednio do tej klasy.

## <a name="related-classes"></a>Klasy pokrewne

[CLongBinary](../mfc/reference/clongbinary-class.md)<br/>
Hermetyzuje dojścia do magazynu w celu duży obiekt binarny (BLOB), takie jak mapy bitowej. `CLongBinary` obiekty są używane do zarządzania obiektami dużych ilości danych przechowywanych w tabelach bazy danych.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Otoka dla typu automatyzacji OLE **waluty**, stałoprzecinkowa typ arytmetyczny, z 15 cyfr przed przecinkiem dziesiętnym i 4 cyfr po.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Otoka dla typu automatyzacji OLE **data**. Reprezentuje wartości daty i godziny.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Otoka dla typu automatyzacji OLE **VARIANT**. Dane w **VARIANT**s mogą być przechowywane w wielu formatach.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../mfc/class-library-overview.md)
