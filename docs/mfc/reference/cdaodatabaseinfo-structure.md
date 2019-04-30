---
title: CDaoDatabaseInfo — Struktura
ms.date: 11/04/2016
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 920301af6f660aeac010ecbf844b80ea628bbfd7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405771"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo — Struktura

`CDaoDatabaseInfo` Struktura zawiera informacje dotyczące obiektu bazy danych zdefiniowanych dla obiektów dostępu do danych (DAO).

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
Unikatowej nazwy obiektu bazy danych. Aby bezpośrednio pobrać tę właściwość, należy wywołać [CDaoDatabase::GetName](../../mfc/reference/cdaodatabase-class.md#getname). Aby uzyskać szczegółowe informacje zobacz temat "Nazwa właściwości" w Pomocy programu DAO.

*m_bUpdatable*<br/>
Wskazuje, czy zmiany mogą być tworzone w bazie danych. Aby bezpośrednio pobrać tę właściwość, należy wywołać [CDaoDatabase::CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate). Aby uzyskać szczegółowe informacje zobacz temat "Można zaktualizować właściwości" w Pomocy programu DAO.

*m_bTransactions*<br/>
Wskazuje, czy źródło danych obsługuje transakcje — nagrywanie szereg zmian, które można później wycofana (anulowane) lub zatwierdzić (zapisane). Jeśli bazy danych jest oparta na aparacie bazy danych Microsoft Jet, właściwości transakcji jest różna od zera, a następnie można użyć transakcji. Inne aparaty bazy danych może nie obsługuje transakcji. Aby bezpośrednio pobrać tę właściwość, należy wywołać [CDaoDatabase::CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact). Aby uzyskać szczegółowe informacje zobacz temat "Property transakcji" w Pomocy programu DAO.

*m_strVersion*<br/>
Wskazuje wersję aparatu bazy danych Microsoft Jet. Aby bezpośrednio pobrać wartość tej właściwości, należy wywołać obiekt bazy danych [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) funkcja elementu członkowskiego. Aby uzyskać szczegółowe informacje zobacz temat "Właściwość Version" w Pomocy programu DAO.

*m_lCollatingOrder*<br/>
Określa sekwencję porządek sortowania w tekście do porównywania ciągów i sortowania. Możliwe wartości obejmują:

- `dbSortGeneral` Użyj ogólnych kolejności sortowania (angielskim, francuskim, niemieckim, portugalskim, włoski i hiszpański nowoczesnych).

- `dbSortArabic` Kolejność sortowania w języku arabskim.

- `dbSortCyrillic` Użyj kolejności sortowania rosyjski.

- `dbSortCzech` Użyj kolejności sortowania czeski.

- `dbSortDutch` Użyj kolejności sortowania Dutch.

- `dbSortGreek` Użyj kolejności sortowania greckich.

- `dbSortHebrew` Użyj kolejności sortowania hebrajski.

- `dbSortHungarian` Użyj kolejności sortowania Węgierskiej.

- `dbSortIcelandic` Użyj kolejności sortowania islandzkim.

- `dbSortNorwdan` Użyj kolejności sortowania norweski lub korona.

- `dbSortPDXIntl` Użyj Paradox International kolejności sortowania.

- `dbSortPDXNor` Użyj Paradox norweski lub kolejności sortowania korona.

- `dbSortPDXSwe` Użyj Paradox korona lub kolejności sortowania fiński.

- `dbSortPolish` Użyj kolejności sortowania Polski.

- `dbSortSpanish` Użyj kolejności sortowania hiszpański.

- `dbSortSwedFin` Użyj kolejności sortowania korona lub fiński.

- `dbSortTurkish` Użyj kolejności sortowania turecki.

- `dbSortUndefined` Kolejność sortowania jest wartością nieokreśloną lub nieznany.

Aby uzyskać więcej informacji zobacz temat "Dostosowywanie Windows rejestru ustawień do Data Access" w Pomocy programu DAO.

*m_nQueryTimeout*<br/>
Liczba sekund oczekiwania przez aparat bazy danych Microsoft Jet przed błąd upływu limitu czasu występuje, gdy zapytanie jest uruchamiany na bazy danych ODBC. Domyślna wartość limitu czasu wynosi 60 sekund. Gdy QueryTimeout jest równa 0, następuje limitu czasu; może to spowodować, że program przestanie odpowiadać. Aby bezpośrednio pobrać wartość tej właściwości, należy wywołać obiekt bazy danych [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) funkcja elementu członkowskiego. Aby uzyskać szczegółowe informacje zobacz temat "QueryTimeout Property" w Pomocy programu DAO.

*m_strConnect*<br/>
Zawiera informacje o źródle otwartą bazę danych. Uzyskać informacji o łączenie ciągów i uzyskać informacji o pobieraniu wartość tej właściwości bezpośrednio, zobacz [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) funkcja elementu członkowskiego. Aby uzyskać więcej informacji zobacz temat "Connect Property" w Pomocy programu DAO.

## <a name="remarks"></a>Uwagi

Baza danych znajduje się obiekt DAO MFC obiekt klasy bazowe [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Odwołania do podstawowego, pomocniczego i wszystkie powyższe wskazują, jak informacji jest zwróconych przez [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) funkcja elementu członkowskiego.

Informacje o pobrane przez [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) funkcja członkowska jest przechowywany w `CDaoDatabaseInfo` struktury. Wywołaj `GetDatabaseInfo` dla `CDaoWorkspace` obiekt, w których zbieranie baz danych jest przechowywany obiekt bazy danych. `CDaoDatabaseInfo` definiuje również `Dump` kompilacje funkcja elementu członkowskiego podczas debugowania. Możesz użyć `Dump` do porzucenia zawartość `CDaoDatabaseInfo` obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdao.h

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)<br/>
[Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)
