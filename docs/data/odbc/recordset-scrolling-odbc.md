---
title: 'Zestaw rekordów: przewijanie (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets [C++], end of
- recordsets [C++], beginning of
- navigation [C++], recordsets
- recordsets [C++], moving to records
- ODBC recordsets, scrolling
- recordsets [C++], navigating
- scrolling [C++], recordsets
- Move method (recordsets)
ms.assetid: f38d2dcb-1e88-4e41-af25-98b00c276be4
ms.openlocfilehash: 931051296dff495939fcbd894102a1b00e48ee90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366940"
---
# <a name="recordset-scrolling-odbc"></a>Zestaw rekordów: przewijanie (ODBC)

Ten temat dotyczy klas MFC ODBC.

Po otwarciu zestawie rekordów należy uzyskać dostęp do rekordów, aby wyświetlić wartości, wykonać obliczenia, wygenerować raporty itd. Przewijanie umożliwia przejście z rekordu do nagrywania w komecie rekordów.

W tym temacie wyjaśniono:

- [Jak przewijać z jednego rekordu do drugiego w ach.](#_core_scrolling_from_one_record_to_another)

- [W jakich okolicznościach przewijanie jest i nie jest obsługiwane](#_core_when_scrolling_is_supported).

## <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>Przewijanie z jednego rekordu do drugiego

Klasa `CRecordset` udostępnia `Move` funkcje członkowskie do przewijania w obrębie pliku recordset. Te funkcje przenoszą bieżący rekord według zestawów wierszy. Jeśli zaimplementowano pobieranie wiersza zbiorczego, `Move` operacja zmienia położenie zestawu rekordów o rozmiar zestawu wierszy. Jeśli pobieranie wiersza zbiorczego nie zostało zaimplementowane, wywołanie `Move` funkcji zmienia położenie zestawie rekordów za każdym razem o jeden rekord. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [Rekord rekordów: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
> Podczas przechodzenia przez plan rekordów usunięte rekordy mogą nie zostać pominięte. Aby uzyskać więcej informacji, zobacz [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) funkcji elementu członkowskiego.

Oprócz `Move` funkcji udostępnia `CRecordset` funkcje członkowskie do sprawdzania, czy przewijanie poza końcem lub przed rozpoczęciem pliku recordset.

Aby ustalić, czy przewijanie jest `CanScroll` możliwe w pliku recordset, należy wywołać funkcję elementu członkowskiego.

#### <a name="to-scroll"></a>Aby przewinąć

1. Prześlij dalej jeden rekord lub jeden zestaw wierszy: wywołaj funkcję [MoveNext.](../../mfc/reference/crecordset-class.md#movenext)

1. Wstecz jeden rekord lub jeden zestaw wierszy: wywołaj funkcję elementu członkowskiego [MovePrev.](../../mfc/reference/crecordset-class.md#moveprev)

1. Do pierwszego rekordu w pliku recordset: wywołaj funkcję [MoveFirst](../../mfc/reference/crecordset-class.md#movefirst) member.

1. Do ostatniego rekordu w zestawie rekordów lub do ostatniego zestawu wierszy: wywołaj funkcję [MoveLast](../../mfc/reference/crecordset-class.md#movelast) element członkowski.

1. *Rekordy N* względem bieżącej pozycji: wywołaj funkcję [Przenieś](../../mfc/reference/crecordset-class.md#move) element członkowski.

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>Aby przetestować koniec lub początek

1. Czy przewinąłeś obok ostatniego rekordu? Wywołanie funkcji elementu członkowskiego [IsEOF.](../../mfc/reference/crecordset-class.md#iseof)

1. Czy przewinąłeś przed pierwszym rekordem (przesuwając się do tyłu)? Wywołanie funkcji elementu członkowskiego [IsBOF.](../../mfc/reference/crecordset-class.md#isbof)

Poniższy przykład kodu `IsBOF` `IsEOF` używa i do wykrywania limitów pliku recordset podczas przewijania w obu kierunkach.

```
// Open a recordset; first record is current
CCustSet rsCustSet( NULL );
rsCustSet.Open( );

if( rsCustSet.IsBOF( ) )
    return;
    // The recordset is empty

// Scroll to the end of the recordset, past
// the last record, so no record is current
while ( !rsCustSet.IsEOF( ) )
    rsCustSet.MoveNext( );

// Move to the last record
rsCustSet.MoveLast( );

// Scroll to beginning of the recordset, before
// the first record, so no record is current
while( !rsCustSet.IsBOF( ) )
    rsCustSet.MovePrev( );

// First record is current again
rsCustSet.MoveFirst( );
```

`IsEOF`zwraca wartość niezerową, jeśli grupa rekordów znajduje się poza ostatnim rekordem. `IsBOF`zwraca wartość niezerową, jeśli grupa rekordów znajduje się przed pierwszym rekordem (przed wszystkimi rekordami). W obu przypadkach nie ma bieżącego rekordu do działania. Jeśli `MovePrev` wywołasz, gdy `IsBOF` jest `MoveNext` `IsEOF` już prawda lub wywołać, `CDBException`gdy jest już true, framework rzuca . Można również `IsBOF` użyć `IsEOF` i sprawdzić, czy nie ma pustego pliku recordset.

Aby uzyskać więcej informacji na temat nawigacji w forsach [rekordów, zobacz Tablica rekordów: Zakładki i Pozycje bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>Gdy przewijanie jest obsługiwane

Zgodnie z pierwotnym projektem SQL pod warunkiem tylko przewijanie do przodu, ale ODBC rozszerza możliwości przewijania. Dostępny poziom obsługi przewijania zależy od sterowników ODBC, z które działa aplikacja, poziomu zgodności interfejsu API odbc sterownika oraz od tego, czy biblioteka kursora ODBC jest ładowana do pamięci. Aby uzyskać więcej informacji, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!TIP]
> Można kontrolować, czy biblioteka kursorów jest używana. Zobacz parametry *bUseCursorLib* i *dwOptions* do [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open).

> [!NOTE]
> W przeciwieństwie do klas DAO MFC klasy Odbc MFC nie zapewniają zestaw `Find` funkcji do lokalizowania następnego (lub poprzedniego) rekordu, który spełnia określone kryteria.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[Zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
