---
title: CDaoDatabaseInfo — Struktura
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 60972aa3ecaef4d38c9a0d0ecc70477796aa37aa
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74304255"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo — Struktura

Struktura `CDaoDatabaseInfo` zawiera informacje o obiekcie bazy danych zdefiniowanym dla obiektów dostępu do danych (DAO). Element DAO 3,6 jest wersją ostateczną i jest uznawany za przestarzały.

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

- `dbSortGeneral` użyć porządku sortowania General (angielski, francuski, niemiecki, portugalski, włoski i współczesny).

- `dbSortArabic` użyć kolejnooci sortowania w języku arabskim.

- `dbSortCyrillic` użyć rosyjskiej kolejności sortowania.

- `dbSortCzech` użyć kolejności sortowania czeskiego.

- `dbSortDutch` użyć kolejności sortowania holenderskiego.

- `dbSortGreek` użyć greckiego porządku sortowania.

- `dbSortHebrew` użyć porządku sortowania w języku hebrajskim.

- `dbSortHungarian` użyć kolejności sortowania węgierskiej.

- `dbSortIcelandic` użyć porządku sortowania islandzkiego.

- `dbSortNorwdan` użyć kolejności sortowania norweskiej lub duńskiej.

- `dbSortPDXIntl` używać międzynarodowej kolejności sortowania programu Paradox.

- `dbSortPDXNor` użyć w programie Paradox norweski lub duński porządek sortowania.

- `dbSortPDXSwe` użyć w programie Paradox szwedzki lub fiński porządek sortowania.

- `dbSortPolish` użyć porządku sortowania polskiego.

- `dbSortSpanish` użyć hiszpańskiej kolejności sortowania.

- `dbSortSwedFin` użyć szwedzkiej lub fińskiej kolejności sortowania.

- `dbSortTurkish` używać tureckiej kolejności sortowania.

- `dbSortUndefined` kolejność sortowania jest niezdefiniowana lub nieznana.

Aby uzyskać więcej informacji, zobacz temat "Dostosowywanie ustawień rejestru systemu Windows na potrzeby dostępu do danych" w pomocy DAO.

*m_nQueryTimeout*<br/>
Liczba sekund oczekiwania przez aparat bazy danych Microsoft Jet przed wystąpieniem błędu limitu czasu, gdy zapytanie zostanie uruchomione w bazie danych ODBC. Domyślna wartość limitu czasu to 60 sekund. Gdy wartość QueryTimeout jest równa 0, nie ma limitu czasu. może to spowodować, że program przestanie odpowiadać. Aby bezpośrednio pobrać wartość tej właściwości, wywołaj funkcję członkowską [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) obiektu bazy danych. Aby uzyskać szczegółowe informacje, zobacz temat "Właściwość QueryTimeout" w pomocy DAO.

*m_strConnect*<br/>
Zawiera informacje o źródle otwartej bazy danych. Aby uzyskać informacje o ciągach połączeń i informacje o tym, jak bezpośrednio pobrać wartość tej właściwości, zobacz funkcja członkowska [CDaoDatabase:: GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) . Aby uzyskać więcej informacji, zobacz temat "Connect Property" w pomocy DAO.

## <a name="remarks"></a>Uwagi

Baza danych jest obiektem DAO, który jest obiektem MFC klasy [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Odwołania do elementów podstawowych, pomocniczych i wszystkie powyżej wskazują, jak informacje są zwracane przez funkcję członkowską [CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) .

Informacje pobierane przez funkcję członkowską [CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) są przechowywane w strukturze `CDaoDatabaseInfo`. Wywołaj `GetDatabaseInfo` dla obiektu `CDaoWorkspace`, w którym jest przechowywany obiekt bazy danych w kolekcji baz danych. `CDaoDatabaseInfo` również definiuje funkcję członkowską `Dump` w kompilacjach debugowania. Aby zrzucić zawartość obiektu `CDaoDatabaseInfo`, można użyć `Dump`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao. h

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)
