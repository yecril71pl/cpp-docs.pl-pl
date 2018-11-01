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
ms.openlocfilehash: e41b526b86922bafd1d923fa5848a5ef8ed4825e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579610"
---
# <a name="recordset-scrolling-odbc"></a>Zestaw rekordów: przewijanie (ODBC)

Ten temat dotyczy klas MFC ODBC.

Zestaw rekordów został otwarty, możesz potrzebujesz dostępu do rekordów do wyświetlenia wartości, wykonywania obliczeń, generowanie raportów i tak dalej. Przewijanie pozwala przenosić między rekordami w twoim zestawie rekordów.

W tym temacie opisano:

- [Jak przewijać z jednego rekordu do drugiego w zestawie rekordów](#_core_scrolling_from_one_record_to_another).

- [W obszarze co okoliczności przewijania jest i nie jest obsługiwana](#_core_when_scrolling_is_supported).

##  <a name="_core_scrolling_from_one_record_to_another"></a> Przewijanie z jednego rekordu do innego

Klasa `CRecordset` zapewnia `Move` funkcji elementów członkowskich do przewijania w zestawie rekordów. Te funkcje przenieść bieżący rekord zestawów wierszy. Jeśli zaimplementowano zbiorcze pobieranie z wiersza, `Move` operacja powoduje przeniesienie zestawu rekordów według rozmiaru zestawu wierszy. Jeśli nie zaimplementowano wiersz zbiorcze pobieranie wywołanie `Move` funkcji powoduje przeniesienie zestaw rekordów w jednym rekordzie każdorazowo. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów w zbiorcze (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Podczas przechodzenia przez zestaw rekordów, usuniętych rekordów nie mogły zostać pominięte. Aby uzyskać więcej informacji, zobacz [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) funkcja elementu członkowskiego.

Oprócz `Move` funkcji `CRecordset` dostarcza funkcji elementów członkowskich do sprawdzania, czy były przewijane poza końcem lub w przód od początku rekordów.

Aby ustalić, czy przewijanie jest możliwe w twoim zestawie rekordów, należy wywołać `CanScroll` funkcja elementu członkowskiego.

#### <a name="to-scroll"></a>Aby przewijać

1. Przekazuj jeden rekord lub jednego zestawu wierszy: wywołanie [MoveNext](../../mfc/reference/crecordset-class.md#movenext) funkcja elementu członkowskiego.

1. Z poprzednimi wersjami jeden rekord lub jednego zestawu wierszy: wywołanie [moveprev —](../../mfc/reference/crecordset-class.md#moveprev) funkcja elementu członkowskiego.

1. Do pierwszego rekordu w zestawie rekordów: wywołanie [MoveFirst](../../mfc/reference/crecordset-class.md#movefirst) funkcja elementu członkowskiego.

1. Ostatni rekord w zestawie lub ostatni zestaw wierszy: wywołanie [MoveLast](../../mfc/reference/crecordset-class.md#movelast) funkcja elementu członkowskiego.

1. *N* rekordów względem bieżącego położenia: wywołanie [przenieść](../../mfc/reference/crecordset-class.md#move) funkcja elementu członkowskiego.

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>Aby przetestować koniec lub początek zestawu rekordów

1. Masz przewiniesz po ostatnim rekordzie? Wywołaj [IsEOF](../../mfc/reference/crecordset-class.md#iseof) funkcja elementu członkowskiego.

1. Masz przewiniesz w przód od pierwszego rekordu (przenoszenie do tyłu)? Wywołaj [IsBOF](../../mfc/reference/crecordset-class.md#isbof) funkcja elementu członkowskiego.

Poniższy przykład kodu wykorzystuje `IsBOF` i `IsEOF` wykrywania limity zestawu rekordów podczas przewijania w dowolnym kierunku.

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

`IsEOF` Zwraca wartość różną od zera, jeśli zestaw rekordów jest umieszczany po ostatnim rekordzie. `IsBOF` Zwraca wartość różną od zera, jeśli zestaw rekordów jest umieszczony przed pierwszym rekordzie (przed wszystkie rekordy). W obu przypadkach nie istnieje bieżący rekord do wykonywania operacji. Jeśli wywołasz `MovePrev` podczas `IsBOF` jest już wartość TRUE, lub zadzwoń `MoveNext` podczas `IsEOF` już ma wartość TRUE, w ramach zgłasza `CDBException`. Można również użyć `IsBOF` i `IsEOF` pod kątem pusty zestaw rekordów.

Aby uzyskać więcej informacji na temat rekordów nawigacji zobacz [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

##  <a name="_core_when_scrolling_is_supported"></a> Podczas przewijania jest obsługiwana

Pierwotnie zaprojektowane SQL podane tylko do przodu przewijania, ale ODBC rozszerza możliwości przewijania. Dostępny poziom obsługi przewijanie zależy od sterowników ODBC, jeśli aplikacja działa przy użyciu sterowniku stopień zgodności ze standardem interfejsu API ODBC, oraz tego, czy Biblioteka kursorów ODBC jest ładowany do pamięci. Aby uzyskać więcej informacji, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!TIP]
>  Można kontrolować, czy ma być używana z biblioteki kursorów. Zobacz *bUseCursorLib* i *dwOptions* parametry [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open).

> [!NOTE]
>  W przeciwieństwie do klas MFC DAO klasach MFC ODBC nie udostępniają zestaw `Find` funkcje do lokalizowania dalej (lub wcześniejszym) rekord, który spełnia określone kryteria.

## <a name="see-also"></a>Zobacz też

[Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[Zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)