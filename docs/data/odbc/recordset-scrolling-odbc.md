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
ms.openlocfilehash: 8a8305d2acacc79f5d7fe395087a0bd13dcbd196
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212774"
---
# <a name="recordset-scrolling-odbc"></a>Zestaw rekordów: przewijanie (ODBC)

Ten temat dotyczy klas MFC ODBC.

Po otwarciu zestawu rekordów należy uzyskać dostęp do rekordów, aby wyświetlić wartości, wykonywać obliczenia, generować raporty itd. Przewijanie umożliwia przejście z rekordu do rekordu w zestawie rekordów.

W tym temacie objaśniono:

- [Sposób przewijania z jednego rekordu do drugiego w zestawie rekordów](#_core_scrolling_from_one_record_to_another).

- [W obszarze Jakie jest przewijanie i nie jest obsługiwane](#_core_when_scrolling_is_supported).

##  <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a>Przewijanie jednego rekordu do innego

Klasy `CRecordset` udostępniają `Move` funkcje członkowskie do przewijania w ramach zestawu rekordów. Te funkcje przenoszą bieżący rekord przez zestawy wierszy. Jeśli zaimplementowano pobieranie wierszy zbiorczych, operacja `Move` zmienia położenie zestawu rekordów według rozmiaru zestawu wierszy. Jeśli nie zaimplementowano pobierania wierszy zbiorczych, wywołanie funkcji `Move` zmienia położenie zestawu rekordów według jednego rekordu za każdym razem. Aby uzyskać więcej informacji na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Podczas przechodzenia przez zestaw rekordów usunięte rekordy mogą nie zostać pominięte. Aby uzyskać więcej informacji, zobacz Funkcja elementu członkowskiego [isdelete](../../mfc/reference/crecordset-class.md#isdeleted) .

Oprócz funkcji `Move` `CRecordset` udostępnia funkcje członkowskie, aby sprawdzić, czy przewinie się poza końcem lub przed początkiem zestawu rekordów.

Aby określić, czy w zestawie rekordów jest możliwe przewijanie, wywołaj funkcję elementu członkowskiego `CanScroll`.

#### <a name="to-scroll"></a>Aby przewijać

1. Przekazywanie jednego rekordu lub jednego zestawu wierszy: wywoływanie funkcji składowej [MoveNext](../../mfc/reference/crecordset-class.md#movenext) .

1. Jeden rekord z poprzednimi wersjami lub jeden zestaw wierszy: wywołaj funkcję członkowską [MovePrev](../../mfc/reference/crecordset-class.md#moveprev) .

1. Do pierwszego rekordu w zestawie rekordów: wywołaj funkcję członkowską [MoveFirst](../../mfc/reference/crecordset-class.md#movefirst) .

1. Do ostatniego rekordu w zestawie rekordów lub do ostatniego zestawu wierszy: wywołaj funkcję członkowską [MoveLast](../../mfc/reference/crecordset-class.md#movelast) .

1. *N* rekordów względem bieżącego położenia: wywołaj funkcję [przenoszenia](../../mfc/reference/crecordset-class.md#move) elementu członkowskiego.

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>Aby przetestować pod kątem końca lub początku zestawu rekordów

1. Czy wystąpiło przewinięcie ostatniego rekordu? Wywołaj funkcję członkowską [IsEOF](../../mfc/reference/crecordset-class.md#iseof) .

1. Czy po wykonaniu tej operacji przewinięcie pierwszego rekordu (przechodzenie do tyłu)? Wywołaj funkcję członkowską [IsBOF](../../mfc/reference/crecordset-class.md#isbof) .

Poniższy przykład kodu używa `IsBOF` i `IsEOF` do wykrywania limitów zestawu rekordów podczas przewijania w dowolnym kierunku.

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

`IsEOF` zwraca wartość różną od zera, jeśli zestaw rekordów jest umieszczony poza ostatnim rekordem. `IsBOF` zwraca wartość różną od zera, jeśli zestaw rekordów jest umieszczony przed pierwszym rekordem (przed wszystkimi rekordami). W obu przypadkach nie ma bieżącego rekordu do działania. W przypadku wywołania `MovePrev`, gdy `IsBOF` jest już prawdziwy, lub wywoływać `MoveNext` gdy `IsEOF` jest już prawdziwe, platforma zgłasza `CDBException`. Można również użyć `IsBOF` i `IsEOF` do sprawdzenia pustego zestawu rekordów.

Aby uzyskać więcej informacji na temat nawigowania po zestawach rekordów, zobacz [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a>Gdy przewijanie jest obsługiwane

Jak pierwotnie zaprojektowano, funkcja SQL udostępnia tylko przewijanie do przodu, ale funkcja ODBC rozszerza możliwości przewijania. Dostępny poziom obsługi przewijania zależy od sterowników ODBC, z którymi działa aplikacja, poziomu zgodności interfejsu API ODBC sterownika oraz tego, czy biblioteka kursorów ODBC jest ładowana do pamięci. Aby uzyskać więcej informacji, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!TIP]
>  Można kontrolować, czy biblioteka kursorów jest używana. Zobacz parametry *bUseCursorLib* i *dwOptions* do [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open).

> [!NOTE]
>  W przeciwieństwie do klas MFC DAO klasy MFC ODBC nie udostępniają zestawu `Find` funkcji do lokalizowania następnego (lub poprzedniego) rekordu spełniającego określone kryteria.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset:: Scroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[Zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
