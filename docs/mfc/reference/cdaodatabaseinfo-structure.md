---
title: Cdaodatabaseinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoDatabaseInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0815d248b6726d830fc50af9886c729c34ba2f29
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336484"
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
 *m_strName*  
 Unikatowej nazwy obiektu bazy danych. Aby bezpośrednio pobrać tę właściwość, należy wywołać [CDaoDatabase::GetName](../../mfc/reference/cdaodatabase-class.md#getname). Aby uzyskać szczegółowe informacje zobacz temat "Nazwa właściwości" w Pomocy programu DAO.  
  
 *m_bUpdatable*  
 Wskazuje, czy zmiany mogą być tworzone w bazie danych. Aby bezpośrednio pobrać tę właściwość, należy wywołać [CDaoDatabase::CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate). Aby uzyskać szczegółowe informacje zobacz temat "Można zaktualizować właściwości" w Pomocy programu DAO.  
  
 *m_bTransactions*  
 Wskazuje, czy źródło danych obsługuje transakcje — nagrywanie szereg zmian, które można później wycofana (anulowane) lub zatwierdzić (zapisane). Jeśli bazy danych jest oparta na aparacie bazy danych Microsoft Jet, właściwości transakcji jest różna od zera, a następnie można użyć transakcji. Inne aparaty bazy danych może nie obsługuje transakcji. Aby bezpośrednio pobrać tę właściwość, należy wywołać [CDaoDatabase::CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact). Aby uzyskać szczegółowe informacje zobacz temat "Property transakcji" w Pomocy programu DAO.  
  
 *m_strVersion*  
 Wskazuje wersję aparatu bazy danych Microsoft Jet. Aby bezpośrednio pobrać wartość tej właściwości, należy wywołać obiekt bazy danych [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) funkcja elementu członkowskiego. Aby uzyskać szczegółowe informacje zobacz temat "Właściwość Version" w Pomocy programu DAO.  
  
 *m_lCollatingOrder*  
 Określa sekwencję porządek sortowania w tekście do porównywania ciągów i sortowania. Możliwe wartości:  
  
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
  
 *m_nQueryTimeout*  
 Liczba sekund oczekiwania przez aparat bazy danych Microsoft Jet przed błąd upływu limitu czasu występuje, gdy zapytanie jest uruchamiany na bazy danych ODBC. Domyślna wartość limitu czasu wynosi 60 sekund. Gdy QueryTimeout jest równa 0, następuje limitu czasu; może to spowodować, że program przestanie odpowiadać. Aby bezpośrednio pobrać wartość tej właściwości, należy wywołać obiekt bazy danych [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) funkcja elementu członkowskiego. Aby uzyskać szczegółowe informacje zobacz temat "QueryTimeout Property" w Pomocy programu DAO.  
  
 *m_strConnect*  
 Zawiera informacje o źródle otwartą bazę danych. Uzyskać informacji o łączenie ciągów i uzyskać informacji o pobieraniu wartość tej właściwości bezpośrednio, zobacz [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) funkcja elementu członkowskiego. Aby uzyskać więcej informacji zobacz temat "Connect Property" w Pomocy programu DAO.  
  
## <a name="remarks"></a>Uwagi  
 Baza danych znajduje się obiekt DAO MFC obiekt klasy bazowe [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Odwołania do podstawowego, pomocniczego i wszystkie powyższe wskazują, jak informacji jest zwróconych przez [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) funkcja elementu członkowskiego.  
  
 Informacje o pobrane przez [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) funkcja członkowska jest przechowywany w `CDaoDatabaseInfo` struktury. Wywołaj `GetDatabaseInfo` dla `CDaoWorkspace` obiekt, w których zbieranie baz danych jest przechowywany obiekt bazy danych. `CDaoDatabaseInfo` definiuje również `Dump` kompilacje funkcja elementu członkowskiego podczas debugowania. Możesz użyć `Dump` do porzucenia zawartość `CDaoDatabaseInfo` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)   
 [Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)
