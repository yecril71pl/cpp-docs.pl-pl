---
title: "Cdaodatabaseinfo — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoDatabaseInfo
dev_langs: C++
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c445d2db084e6148032cfde0c356ad88ad1cccfa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo — Struktura
`CDaoDatabaseInfo` Struktura zawiera informacje dotyczące obiektu bazy danych zdefiniowany dla obiektów dostępu do danych (DAO).  
  
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
 `m_strName`  
 Unikatowej nazwy obiektu bazy danych. Aby bezpośrednio pobrać tę właściwość, należy wywołać [CDaoDatabase::GetName](../../mfc/reference/cdaodatabase-class.md#getname). Aby uzyskać więcej informacji zobacz temat "Właściwości Name" w pomocy DAO.  
  
 `m_bUpdatable`  
 Wskazuje, czy zmiany mogą być tworzone w bazie danych. Aby bezpośrednio pobrać tę właściwość, należy wywołać [CDaoDatabase::CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate). Aby uzyskać więcej informacji zobacz temat "Nadaje się do aktualizacji właściwości" w pomocy DAO.  
  
 *m_bTransactions*  
 Wskazuje, czy źródło danych obsługuje transakcje — nagrania szereg zmian, które później można wycofać (anulowane) lub zatwierdzonej (zapisane). Jeśli bazy danych jest oparta na aparacie bazy danych programu Microsoft Jet, właściwość transakcji jest różna od zera i transakcji można użyć. Innych baz danych może nie obsługuje transakcji. Aby bezpośrednio pobrać tę właściwość, należy wywołać [CDaoDatabase::CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact). Aby uzyskać więcej informacji zobacz temat "Transakcje Property" w pomocy DAO.  
  
 *m_strVersion*  
 Wskazuje wersję aparatu bazy danych programu Microsoft Jet. Aby bezpośrednio pobrać wartości tej właściwości, należy wywołać obiekt bazy danych [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) funkcję elementu członkowskiego. Aby uzyskać więcej informacji zobacz temat "Właściwość Version" w pomocy DAO.  
  
 `m_lCollatingOrder`  
 Określa sekwencję kolejności sortowania w tekście do porównania ciągów i sortowania. Możliwe wartości:  
  
- **dbSortGeneral** Użyj ogólne kolejność sortowania (angielskim, francuskim, niemieckim, portugalski, włoski i hiszpański nowoczesne).  
  
- **dbSortArabic** Arabic sortowanie.  
  
- **dbSortCyrillic** rosyjski sortowanie.  
  
- **dbSortCzech** czeski sortowanie.  
  
- **dbSortDutch** holenderski sortowanie.  
  
- **dbSortGreek** grecki sortowanie.  
  
- **dbSortHebrew** hebrajski sortowanie.  
  
- **dbSortHungarian** Węgierskiej sortowanie.  
  
- **dbSortIcelandic** islandzkim sortowanie.  
  
- **dbSortNorwdan** norweski lub duński sortowanie.  
  
- **dbSortPDXIntl** Użyj międzynarodowej Paradox kolejności sortowania.  
  
- **dbSortPDXNor** Paradox norweski lub duński sortowania.  
  
- **dbSortPDXSwe** Paradox szwedzki lub fiński sortowania.  
  
- **dbSortPolish** Polski sortowanie.  
  
- **dbSortSpanish** hiszpańskim sortowanie.  
  
- **dbSortSwedFin** szwedzki lub fiński sortowanie.  
  
- **dbSortTurkish** tureckiego sortowanie.  
  
- **dbSortUndefined** kolejność sortowania jest niezdefiniowana lub nieznany.  
  
 Aby uzyskać więcej informacji zobacz temat "Dostosowywanie systemu Windows rejestru ustawienia dla Data Access" w pomocy DAO.  
  
 *m_nQueryTimeout*  
 Liczba sekund oczekiwania przed błąd upływu limitu czasu aparatu bazy danych programu Microsoft Jet występuje podczas wykonywania kwerendy w bazie danych ODBC. Domyślna wartość limitu czasu wynosi 60 sekund. Gdy QueryTimeout jest ustawiona na 0, nie przekroczony limit czasu; może to spowodować, że program może przestać odpowiadać. Aby bezpośrednio pobrać wartości tej właściwości, należy wywołać obiekt bazy danych [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) funkcję elementu członkowskiego. Aby uzyskać więcej informacji zobacz temat "QueryTimeout Property" w pomocy DAO.  
  
 `m_strConnect`  
 Zawiera informacje o źródle otwartą bazę danych. Informacje o ciągów połączenia i informacje bezpośrednio do pobrania wartości tej właściwości, zobacz [CDaoDatabase::GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) funkcję elementu członkowskiego. Aby uzyskać więcej informacji zobacz temat "Połącz Property" w pomocy DAO.  
  
## <a name="remarks"></a>Uwagi  
 Baza danych jest obiektem DAO MFC obiekt klasy podstawowej [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md). Odwołania do podstawowej, pomocniczej i wszystkie powyższe wskazują, jak informacje zwracane przez [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) funkcję elementu członkowskiego.  
  
 Informacje o pobrane przez [CDaoWorkspace::GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) funkcja członkowska jest przechowywany w `CDaoDatabaseInfo` struktury. Wywołanie `GetDatabaseInfo` dla `CDaoWorkspace` obiektu, w których bazy danych kolekcji jest obiekt bazy danych. `CDaoDatabaseInfo`definiuje również `Dump` kompilacje funkcji członkowskiej podczas debugowania. Można użyć `Dump` do zrzutu zawartość `CDaoDatabaseInfo` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)   
 [Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)
