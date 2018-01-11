---
title: "Zestaw rekordów: Przewijanie (ODBC) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 34dcfb9cb1d45710accba2ee6155e3c741b727be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-scrolling-odbc"></a>Zestaw rekordów: przewijanie (ODBC)
Ten temat dotyczy klasach MFC ODBC.  
  
 Po otwarciu zestawu rekordów, możesz wymagają dostępu do rekordów do wyświetlania wartości, wykonywania obliczeń, generowanie raportów itd. Przewijanie umożliwia przenoszenie z rekordami w ramach zestawu rekordów.  
  
 W tym temacie opisano:  
  
-   [Jak przewiń z jednego rekordu do innego w zestawie rekordów](#_core_scrolling_from_one_record_to_another).  
  
-   [W obszarze co okoliczności przewijanie jest i nie jest obsługiwana](#_core_when_scrolling_is_supported).  
  
##  <a name="_core_scrolling_from_one_record_to_another"></a>Przewijania z jednego rekordu  
 Klasa `CRecordset` zapewnia **Przenieś** funkcji elementów członkowskich do przewijania w zestawie rekordów. Te funkcje Przenieś bieżącego rekordu za pomocą zestawów wierszy. Jeśli zaimplementowano zbiorcze pobieranie z wiersza, **Przenieś** operacji zmiana zestawu rekordów według rozmiaru zestawu wierszy. Jeśli nie zaimplementowano wiersza zbiorcze pobieranie wywołanie **Przenieś** funkcja powoduje przeniesienie zestawu rekordów w jednym rekordzie zawsze. Aby uzyskać więcej informacji na temat zbiorcze pobieranie z wiersza, zobacz [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Podczas przenoszenia za pomocą zestawu rekordów, usuniętych rekordów nie mogły zostać pominięte. Aby uzyskać więcej informacji, zobacz [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) funkcję elementu członkowskiego.  
  
 Oprócz **Przenieś** funkcje `CRecordset` udostępnia funkcje Członkowskie sprawdzania, czy były przewijane poza koniec lub przed początek zestawu rekordów.  
  
 Aby ustalić, czy przewijanie jest możliwe w zestawu rekordów, należy wywołać `CanScroll` funkcję elementu członkowskiego.  
  
#### <a name="to-scroll"></a>Przewijanie  
  
1.  Przekazuj jeden rekord lub jednego zestawu wierszy: wywołanie [MoveNext](../../mfc/reference/crecordset-class.md#movenext) funkcji członkowskiej.  
  
2.  Jeden rekord z poprzednimi wersjami lub jednego zestawu wierszy: wywołanie [MovePrev](../../mfc/reference/crecordset-class.md#moveprev) funkcję elementu członkowskiego.  
  
3.  Na pierwszy rekord w zestawie rekordów: wywołanie [MoveFirst](../../mfc/reference/crecordset-class.md#movefirst) funkcję elementu członkowskiego.  
  
4.  Ostatni rekord w zestawie lub ostatnich wierszy: wywołanie [MoveLast](../../mfc/reference/crecordset-class.md#movelast) funkcję elementu członkowskiego.  
  
5.  *N* rekordów względem bieżącego położenia: wywołanie [Przenieś](../../mfc/reference/crecordset-class.md#move) funkcji członkowskiej.  
  
#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>Próba na końcu lub początku zestawu rekordów  
  
1.  Były przewijane poza ostatni rekord? Wywołanie [IsEOF](../../mfc/reference/crecordset-class.md#iseof) funkcję elementu członkowskiego.  
  
2.  Były przewijane wcześniejsze pierwszy rekord (przechodzenia wstecz)? Wywołanie [IsBOF](../../mfc/reference/crecordset-class.md#isbof) funkcję elementu członkowskiego.  
  
 Poniższy przykład kodu wykorzystuje `IsBOF` i `IsEOF` do wykrywania limitów zestawu rekordów podczas przewijania w żadnym kierunku.  
  
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
  
 `IsEOF`Zwraca wartość niezerową, jeśli zestaw znajduje się poza ostatniego rekordu. `IsBOF`Zwraca wartość niezerową, jeśli zestaw rekordów jest ustawiony przed pierwszym rekordu (przed wszystkie rekordy). W obu przypadkach nie ma bieżącego rekordu do działania na. Wywołanie `MovePrev` podczas `IsBOF` jest już **TRUE** lub zadzwoń `MoveNext` podczas `IsEOF` jest już **TRUE**, zgłasza wyjątek w ramach `CDBException`. Można również użyć `IsBOF` i `IsEOF` do sprawdzenia pusty zestaw rekordów.  
  
 Aby uzyskać więcej informacji na temat nawigacji zestawu rekordów, zobacz [zestaw rekordów: zakładki i położenia bezwzględne (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).  
  
##  <a name="_core_when_scrolling_is_supported"></a>Podczas przewijania jest obsługiwane  
 Pierwotnie zaprojektowanego SQL podane tylko do przodu przewijania, ale ODBC rozszerza możliwości przewijania. Dostępny poziom obsługi przewijanie zależy od sterowników ODBC aplikacja działa z poziomu zgodności interfejsu API ODBC w sterowniku, i określa, czy Biblioteka kursorów ODBC jest ładowany do pamięci. Aby uzyskać więcej informacji, zobacz [ODBC](../../data/odbc/odbc-basics.md) i [ODBC: Biblioteka kursorów ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
> [!TIP]
>  Można kontrolować, czy jest używana z biblioteki kursorów. Zobacz `bUseCursorLib` i `dwOptions` parametry [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open).  
  
> [!NOTE]
>  W przeciwieństwie do klas MFC DAO klasach MFC ODBC nie udostępniają zestaw **znaleźć** funkcje do lokalizowania rekord next (lub wcześniejszym), który spełnia określone kryteria.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::CanScroll](../../mfc/reference/crecordset-class.md#canscroll)   
 [CRecordset::CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)   
 [Zestaw rekordów: filtrowanie rekordów (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)