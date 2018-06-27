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
ms.openlocfilehash: 80c1422c4d0e45599ca8bc2e9c86a4263b8ac9b6
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955612"
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
 Unikatowej nazwy obiektu tabledef. Aby bezpośrednio pobrać wartości tej właściwości, należy wywołać obiekt tabledef [GetName](../../mfc/reference/cdaotabledef-class.md#getname) funkcję elementu członkowskiego. Aby uzyskać więcej informacji zobacz temat "Właściwości Name" w pomocy DAO.  
  
 *m_bUpdatable*  
 Wskazuje, czy zmiany mogą być tworzone w tabeli. Szybkie ustalenie, czy tabela jest aktualizowalny jest otwarcie `CDaoTableDef` obiektu dla tabeli i wywołania obiektu [CanUpdate](../../mfc/reference/cdaotabledef-class.md#canupdate) funkcję elementu członkowskiego. `CanUpdate` zawsze zwraca wartość niezerową (**TRUE**) dla obiekt tabledef nowo utworzona i 0 (**FALSE**) dla obiekt tabledef dołączone. Nowy obiekt tabledef można dołączać tylko do bazy danych, dla którego bieżący użytkownik ma uprawnienia do zapisu. Jeśli tabela zawiera tylko pola nonupdatable `CanUpdate` zwraca wartość 0. Gdy nadaje się do aktualizacji, co najmniej jedno pole `CanUpdate` zwraca różną od zera. Można edytować tylko pola nadaje się do aktualizacji. Aby uzyskać więcej informacji zobacz temat "Nadaje się do aktualizacji właściwości" w pomocy DAO.  
  
 *m_lAttributes*  
 Określa charakterystykę reprezentowanych przez obiekt tabledef tabeli. Aby pobrać bieżące atrybuty tabledef, należy wywołać jej [GetAttributes](../../mfc/reference/cdaotabledef-class.md#getattributes) funkcję elementu członkowskiego. Wartość zwracana może być kombinacji tych długi stałych (przy użyciu wartości bitowe lub (**&#124;**) operatora):  
  
- **dbAttachExclusive** dla baz danych, które używają aparatu bazy danych programu Microsoft Jet wskazuje tabela jest otwarta w trybie wyłączności dołączonej tabeli.  
  
- **dbAttachSavePWD** dla baz danych, które używają aparatu bazy danych programu Microsoft Jet wskazuje, czy identyfikator użytkownika i hasło dla dołączonej tabeli są zapisywane z informacjami o połączeniu.  
  
- **dbSystemObject** wskazuje tabela jest tabelą systemową dostarczone przez aparat bazy danych programu Microsoft Jet. (Tylko do odczytu).  
  
- **dbHiddenObject** wskazuje jest tabela ukryte, dostarczone przez aparat bazy danych programu Microsoft Jet (na potrzeby używania tymczasowe). (Tylko do odczytu).  
  
- **dbAttachedTable** wskazuje jest dołączona tabela z bazy danych z systemem innym niż ODBC, takich jak Paradox bazy danych.  
  
- **dbAttachedODBC** wskazuje jest dołączona tabela z bazy danych ODBC, takich jak Microsoft SQL Server.  
  
 *m_dateCreated*  
 Data i godzina utworzenia tabeli. Aby bezpośrednio pobrać datę utworzenia tabeli, należy wywołać [GetDateCreated](../../mfc/reference/cdaotabledef-class.md#getdatecreated) funkcji członkowskiej klasy `CDaoTableDef` obiekt skojarzony z tabelą. Aby uzyskać więcej informacji, zobacz uwagi poniżej. Powiązane informacje zobacz temat "DateCreated właściwości LastUpdated" w pomocy DAO.  
  
 *m_dateLastUpdated*  
 Data i godzina ostatniej zmiany wprowadzone w projekcie tabeli. Aby bezpośrednio pobrać datę ostatniej aktualizacji tabeli, należy wywołać [GetDateLastUpdated](../../mfc/reference/cdaotabledef-class.md#getdatelastupdated) funkcji członkowskiej klasy `CDaoTableDef` obiekt skojarzony z tabelą. Aby uzyskać więcej informacji, zobacz uwagi poniżej. Powiązane informacje zobacz temat "DateCreated właściwości LastUpdated" w pomocy DAO.  
  
 *m_strSrcTableName*  
 Określa nazwę dołączonej tabeli, jeśli istnieje. Aby bezpośrednio pobrać nazwy tabeli źródłowej, należy wywołać [GetSourceTableName](../../mfc/reference/cdaotabledef-class.md#getsourcetablename) funkcji członkowskiej klasy `CDaoTableDef` obiekt skojarzony z tabelą.  
  
 *m_strConnect*  
 Zawiera informacje o źródle otwartą bazę danych. Tej właściwości można sprawdzić przez wywołanie metody [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) funkcji członkowskiej klasy użytkownika `CDaoTableDef` obiektu. Aby uzyskać więcej informacji na temat ciągów połączenia, zobacz `GetConnect`.  
  
 *m_strValidationRule*  
 Wartość, która weryfikuje dane w polach tabledef, ponieważ są one zmienione lub dodane do tabeli. Walidacja jest obsługiwany tylko w przypadku baz danych, które używają aparatu bazy danych programu Microsoft Jet. Aby bezpośrednio pobrać reguły sprawdzania poprawności, należy wywołać [GetValidationRule](../../mfc/reference/cdaotabledef-class.md#getvalidationrule) funkcji członkowskiej klasy `CDaoTableDef` obiekt skojarzony z tabelą. Powiązane informacje zobacz temat "ValidationRule Property" w pomocy DAO.  
  
 *m_strValidationText*  
 Wartość, która określa tekst wiadomości, która aplikacja powinien być wyświetlany, jeśli nie zostanie spełniony określony przez właściwość ValidationRule reguły weryfikacji. Powiązane informacje zobacz temat "Komunikat Property" w pomocy DAO.  
  
 *m_lRecordCount*  
 Liczba rekordów dostępne w obiekcie tabledef. Ustawienie tej właściwości jest tylko do odczytu. Aby bezpośrednio pobrać liczba rekordów, należy wywołać [GetRecordCount](../../mfc/reference/cdaotabledef-class.md#getrecordcount) funkcji członkowskiej klasy `CDaoTableDef` obiektu. W dokumentacji `GetRecordCount` opisuje dalsze liczba rekordów. Należy pamiętać, że pobieranie ta liczba może być czasochłonna operacja Jeśli tabela zawiera wiele rekordów.  
  
## <a name="remarks"></a>Uwagi  
 Tabledef jest obiektem klasy [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md). Odwołania do podstawowej, pomocniczej i wszystkie powyższe wskazują, jak informacje zwracane przez [GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) funkcji członkowskiej klasy `CDaoDatabase`.  
  
 Informacje o pobrane przez [CDaoDatabase::GetTableDefInfo](../../mfc/reference/cdaodatabase-class.md#gettabledefinfo) funkcja członkowska jest przechowywany w `CDaoTableDefInfo` struktury. Wywołanie `GetTableDefInfo` funkcji członkowskiej klasy `CDaoDatabase` obiektu, w których tabledefs — kolekcja obiekt tabledef jest przechowywany. `CDaoTableDefInfo` definiuje również `Dump` kompilacje funkcji członkowskiej podczas debugowania. Można użyć `Dump` do zrzutu zawartość `CDaoTableDefInfo` obiektu.  
  
 Ustawienia daty i godziny są uzyskiwane z komputera, na którym utworzenia lub ostatniej aktualizacji tabeli podstawowej. W środowisku wielodostępnym użytkowników należy uzyskać te ustawienia bezpośrednio z serwera plików, aby uniknąć niezgodności w DateCreated i LastUpdated ustawienia właściwości.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Klasa CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)   
 [Klasa CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)
