---
title: Cdaotabledefinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoTableDefInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoTableDefInfo structure [MFC]
- DAO (Data Access Objects), TableDefs collection
ms.assetid: c01ccebb-5615-434e-883c-4f60eac943dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac88b3fd55a81237e6c54dbad422f9537950c9e6
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37335767"
---
# <a name="cdaotabledefinfo-structure"></a>CDaoTableDefInfo — Struktura
`CDaoTableDefInfo` Struktura zawiera informacje dotyczące obiektu tabledef zdefiniowany dla obiektów dostępu do danych (DAO).  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CDaoTableDefInfo  
{  
    CString m_strName;               // Primary  
    BOOL m_bUpdatable;               // Primary  
    long m_lAttributes;              // Primary  
    COleDateTime m_dateCreated;      // Secondary  
    COleDateTime m_dateLastUpdated;  // Secondary  
    CString m_strSrcTableName;       // Secondary  
    CString m_strConnect;            // Secondary  
    CString m_strValidationRule;     // All  
    CString m_strValidationText;     // All  
    long m_lRecordCount;             // All  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 *m_strName*  
 Unikatowej nazwy obiektu tabledef. Aby bezpośrednio pobrać wartość tej właściwości, należy wywołać obiekt tabledef [getname —](../../mfc/reference/cdaotabledef-class.md#getname) funkcja elementu członkowskiego. Aby uzyskać więcej informacji zobacz temat "Nazwa właściwości" w Pomocy programu DAO.  
  
 *m_bUpdatable*  
 Wskazuje, czy zmiany mogą być tworzone w tabeli. Szybkim sposobem ustalenia, czy tabela jest nadaje się do aktualizacji jest otwarcie `CDaoTableDef` obiektu dla tabeli i wywołać obiekt [CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate) funkcja elementu członkowskiego. `CanUpdate` zawsze zwraca wartość różną od zera (TRUE) dla obiektu tabledef nowo utworzony i 0 (FALSE) dla obiektu tabledef dołączone. Nowy obiekt tabledef można dołączać tylko do bazy danych, dla którego bieżący użytkownik ma uprawnienia do zapisu. Jeśli tabela zawiera tylko pola nonupdatable `CanUpdate` zwraca wartość 0. W przypadku co najmniej jedno pole nadaje się do aktualizacji, `CanUpdate` zwraca wartość różną od zera. Można edytować tylko pola nadaje się do aktualizacji. Aby uzyskać więcej informacji zobacz temat "Można zaktualizować właściwości" w Pomocy programu DAO.  
  
 *m_lAttributes*  
 Określa właściwości tabeli reprezentowany przez obiekt tabledef. Aby pobrać bieżące atrybuty tabledef, należy wywołać jej [GetAttributes —](../../mfc/reference/cdaotabledef-class.md#getattributes) funkcja elementu członkowskiego. Wartość zwracana może być kombinacją te stałe długi (przy użyciu bitowego lub (**&#124;**) — operator):  
  
- `dbAttachExclusive` W przypadku baz danych, które używają aparatu bazy danych Microsoft Jet wskazuje, że tabela jest otwarty do wyłącznego użytku dołączonej tabeli.  
  
- `dbAttachSavePWD` W przypadku baz danych, które używają aparatu bazy danych Microsoft Jet wskazuje, że identyfikator użytkownika i hasło dla dołączonej tabeli są zapisywane z informacjami o połączeniu.  
  
- `dbSystemObject` Wskazuje, że tabela jest dostarczane przez aparat bazy danych Microsoft Jet tabeli systemowej. (Tylko do odczytu).  
  
- `dbHiddenObject` Wskazuje, że jest tabela ukryte, dostarczone przez aparat bazy danych Microsoft Jet (do tymczasowego użytku). (Tylko do odczytu).  
  
- `dbAttachedTable` Wskazuje, że tabela jest z bazy danych bez ODBC, takich jak bazy danych Paradox dołączonej tabeli.  
  
- `dbAttachedODBC` Wskazuje, że tabela jest dołączonej tabeli z bazy danych ODBC, takich jak Microsoft SQL Server.  
  
 *m_dateCreated*  
 Data i godzina utworzenia tabeli. Aby bezpośrednio pobrać datę utworzenia tabeli, należy wywołać [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) funkcji składowej typu `CDaoTableDef` obiekt skojarzony z tabeli. Aby uzyskać więcej informacji, zobacz uwagi poniżej. Aby uzyskać powiązane informacje zobacz temat "DateCreated LastUpdated właściwości", w Pomocy programu DAO.  
  
 *m_dateLastUpdated*  
 Data i godzina ostatniej zmiany wprowadzone do projektowania tabeli. Aby bezpośrednio pobrać daty ostatniej aktualizacji tabeli, należy wywołać [GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated) funkcji składowej typu `CDaoTableDef` obiekt skojarzony z tabeli. Aby uzyskać więcej informacji, zobacz uwagi poniżej. Aby uzyskać powiązane informacje zobacz temat "DateCreated LastUpdated właściwości", w Pomocy programu DAO.  
  
 *m_strSrcTableName*  
 Określa nazwę dołączonej tabeli, jeśli istnieje. Aby bezpośrednio pobrać nazwy tabeli źródłowej, należy wywołać [GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename) funkcji składowej typu `CDaoTableDef` obiekt skojarzony z tabeli.  
  
 *m_strConnect*  
 Zawiera informacje o źródle otwartą bazę danych. Tej właściwości można sprawdzić przez wywołanie metody [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) funkcji składowej typu usługi `CDaoTableDef` obiektu. Aby uzyskać więcej informacji na temat ciągów połączenia, zobacz `GetConnect`.  
  
 *m_strValidationRule*  
 Wartość, która weryfikuje dane w polach tabledef, ponieważ są one zmienione lub dodane do tabeli. Walidacja jest obsługiwana tylko dla baz danych, które używają aparatu bazy danych Microsoft Jet. Aby bezpośrednio pobrać reguły sprawdzania poprawności, należy wywołać [GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule) funkcji składowej typu `CDaoTableDef` obiekt skojarzony z tabeli. Aby uzyskać powiązane informacje zobacz temat "ValidationRule Property" w Pomocy programu DAO.  
  
 *m_strValidationText*  
 Wartość, która określa tekst komunikatu, który aplikacja powinna być wyświetlana, jeśli reguła sprawdzania poprawności określonej przez właściwość ValidationRule nie został spełniony. Aby uzyskać powiązane informacje zobacz temat "Property komunikat" w Pomocy programu DAO.  
  
 *m_lRecordCount*  
 Liczba rekordów, dostępne w obiekcie tabledef. Ustawienie tej właściwości jest tylko do odczytu. Aby bezpośrednio pobrać liczbę rekordów, należy wywołać [getrecordcount —](../../mfc/reference/cdaotabledef-class.md#getrecordcount) funkcji składowej typu `CDaoTableDef` obiektu. W dokumentacji dotyczącej `GetRecordCount` opisuje dalsze liczba rekordów. Należy pamiętać, że pobieranie ta liczba może być czasochłonna operacja Jeśli tabela zawiera wiele rekordów.  
  
## <a name="remarks"></a>Uwagi  
 Tabledef jest obiektem klasy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Odwołania do podstawowego, pomocniczego i wszystkie powyższe wskazują, jak informacji jest zwróconych przez [GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) funkcja elementu członkowskiego w klasie `CDaoDatabase`.  
  
 Informacje o pobrane przez [CDaoDatabase::GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) funkcja członkowska jest przechowywany w `CDaoTableDefInfo` struktury. Wywołaj `GetTableDefInfo` funkcji składowej typu `CDaoDatabase` obiektu, w których tabledefs — kolekcja jest przechowywany obiekt tabledef. `CDaoTableDefInfo` definiuje również `Dump` kompilacje funkcja elementu członkowskiego podczas debugowania. Możesz użyć `Dump` do porzucenia zawartość `CDaoTableDefInfo` obiektu.  
  
 Ustawienia daty i godziny są uzyskiwane z komputera, na którym został utworzony lub ostatniej aktualizacji tabeli podstawowej. W środowisku wielodostępnym użytkowników należy uzyskać te ustawienia bezpośrednio z serwera plików, aby uniknąć niezgodności w DateCreated i LastUpdated ustawienia właściwości.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)
