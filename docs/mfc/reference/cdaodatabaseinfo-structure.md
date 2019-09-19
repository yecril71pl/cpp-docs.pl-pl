---
title: CDaoDatabaseInfo — Struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 46d8056ee4ab478b65f3ef0bd59d88bd3af9b28c
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71096155"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo — Struktura

`CDaoDatabaseInfo` Struktura zawiera informacje o obiekcie bazy danych zdefiniowanym dla obiektów dostępu do danych (DAO).
Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały.

## <a name="syntax"></a>Składnia

```
struct CDaoDatabaseInfo
{
    CString m_strName;       // Primary
    BOOL m_bUpdatable;       // Primary
    BOOL m_bTransactions;    // Primary
    CString m_strVersion;    // Secondary
    long m_lCollatingOrder;  // Secondary
    short m_nQueryTimeout;   // Secondary
    CString m_strConnect;    // All
};
```

#### <a name="parameters"></a>Parametry

*m_strName*<br/>
Unikatowa nazwa obiektu bazy danych. Aby bezpośrednio pobrać tę właściwość, wywołaj [CDaoDatabase:: GetName](../../mfc/reference/cdaodatabase-class.md#getname). Aby uzyskać szczegółowe informacje, zobacz temat "Nazwa właściwości" w pomocy DAO.

*m_bUpdatable*<br/>
Wskazuje, czy można wprowadzać zmiany w bazie danych. Aby bezpośrednio pobrać tę właściwość, wywołaj [CDaoDatabase:: Update](../../mfc/reference/cdaodatabase-class.md#canupdate). Aby uzyskać szczegółowe informacje, zobacz temat "Aktualizowalna właściwość" w pomocy DAO.

*m_bTransactions*<br/>
Wskazuje, czy źródło danych obsługuje transakcje — nagrywanie serii zmian, które mogą być później wycofywane (anulowane) lub zatwierdzone (zapisane). Jeśli baza danych jest oparta na aparacie bazy danych Microsoft Jet, Właściwość Transactions jest różna od zera i można używać transakcji. Inne aparaty bazy danych mogą nie obsługiwać transakcji. Aby bezpośrednio pobrać tę właściwość, wywołaj [CDaoDatabase:: gettransact](../../mfc/reference/cdaodatabase-class.md#cantransact). Aby uzyskać szczegółowe informacje, zobacz temat "właściwości transakcji" w pomocy DAO.

*m_strVersion*<br/>
Wskazuje wersję aparatu bazy danych Microsoft Jet. Aby bezpośrednio pobrać wartość tej właściwości, wywołaj funkcję elementu członkowskiego [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) obiektu bazy danych. Aby uzyskać szczegółowe informacje, zobacz temat "Właściwość wersji" w pomocy DAO.

*m_lCollatingOrder*<br/>
Określa sekwencję sortowania w tekście dla porównania ciągów lub sortowania. Możliwe wartości obejmują:

- `dbSortGeneral`Użyj porządku sortowania General (angielski, francuski, niemiecki, portugalski, włoski i współczesny).

- `dbSortArabic`Użyj arabskiej kolejności sortowania.

- `dbSortCyrillic`Użyj rosyjskiej kolejności sortowania.

- `dbSortCzech`Użyj zastosowanej kolejności sortowania.

- `dbSortDutch`Użyj kolejności sortowania holenderskiego.

- `dbSortGreek`Użyj greckiej kolejności sortowania.

- `dbSortHebrew`Użyj porządku sortowania w języku hebrajskim.

- `dbSortHungarian`Użyj kolejności sortowania węgierskiej.

- `dbSortIcelandic`Użyj porządku sortowania w języku islandzkim.

- `dbSortNorwdan`Użyj kolejności sortowania w języku norweskim lub duńskim.

- `dbSortPDXIntl`Użyj międzynarodowej kolejności sortowania programu Paradox.

- `dbSortPDXNor`Użyj programu Paradox norweski lub duński porządek sortowania.

- `dbSortPDXSwe`Użyj w programie Paradox szwedzki lub fiński porządek sortowania.

- `dbSortPolish`Użyj porządku sortowania polskiego.

- `dbSortSpanish`Użyj hiszpańskiej kolejności sortowania.

- `dbSortSwedFin`Użyj szwedzkiej lub fińskiej kolejności sortowania.

- `dbSortTurkish`Użyj tureckiej kolejności sortowania.

- `dbSortUndefined`Kolejność sortowania jest niezdefiniowana lub nieznana.

Aby uzyskać więcej informacji, zobacz temat "Dostosowywanie ustawień rejestru systemu Windows na potrzeby dostępu do danych" w pomocy DAO.

*m_nQueryTimeout*<br/>
Liczba sekund oczekiwania przez aparat bazy danych Microsoft Jet przed wystąpieniem błędu limitu czasu, gdy zapytanie zostanie uruchomione w bazie danych ODBC. Domyślna wartość limitu czasu to 60 sekund. Gdy wartość QueryTimeout jest równa 0, nie ma limitu czasu. może to spowodować, że program przestanie odpowiadać. Aby bezpośrednio pobrać wartość tej właściwości, wywołaj funkcję członkowską [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) obiektu bazy danych. Aby uzyskać szczegółowe informacje, zobacz temat "Właściwość QueryTimeout" w pomocy DAO.

*m_strConnect*<br/>
Zawiera informacje o źródle otwartej bazy danych. Aby uzyskać informacje o ciągach połączeń i informacje o tym, jak bezpośrednio pobrać wartość tej właściwości, zobacz funkcja członkowska [CDaoDatabase:: GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) . Aby uzyskać więcej informacji, zobacz temat "Connect Property" w pomocy DAO.

## <a name="remarks"></a>Uwagi

Baza danych jest obiektem DAO, który jest obiektem MFC klasy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Odwołania do elementów podstawowych, pomocniczych i wszystkie powyżej wskazują, jak informacje są zwracane przez funkcję członkowską [CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) .

Informacje pobierane przez funkcję członkowską [CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) są przechowywane w `CDaoDatabaseInfo` strukturze. Wywołanie `GetDatabaseInfo` obiektu, `CDaoWorkspace` w którym jest przechowywany obiekt bazy danych w kolekcji baz danych. `CDaoDatabaseInfo`definiuje również funkcję `Dump` członkowską w kompilacjach debugowania. Możesz użyć `Dump` , aby zrzucić zawartość `CDaoDatabaseInfo` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)
