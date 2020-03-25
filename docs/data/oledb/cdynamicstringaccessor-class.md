---
title: CDynamicStringAccessor — Klasa
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessor
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
helpviewer_keywords:
- CDynamicStringAccessor class
- GetString method
- SetString method
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
ms.openlocfilehash: a0590bc015c5487315b8cbd38f0baf91eb3082cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211872"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor — Klasa

Pozwala uzyskać dostęp do źródła danych, gdy nie ma informacji o schemacie bazy danych (źródłowa struktura bazy danych).

## <a name="syntax"></a>Składnia

```cpp
template< typename BaseType, DBTYPEENUM OleDbType >
class CDynamicStringAccessorT : public CDynamicAccessor
```

## <a name="requirements"></a>Wymagania

**Nagłówek**: atldbcli. h

## <a name="members"></a>Members

### <a name="methods"></a>Metody

|||
|-|-|
|[GetString](#getstring)|Pobiera dane określonego kolumny jako ciąg.|
|[Metodami SetString](#setstring)|Ustawia dane określonego kolumny jako ciąg.|

## <a name="remarks"></a>Uwagi

Podczas gdy [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) żąda danych w formacie natywnym zgłoszonym przez dostawcę, `CDynamicStringAccessor` żądania pobrania przez dostawcę wszystkich danych, do których uzyskano dostęp z magazynu danych jako dane ciągu. Jest to szczególnie przydatne w przypadku prostych zadań, które nie wymagają obliczenia wartości w magazynie danych, na przykład wyświetlania lub drukowania zawartości magazynu danych.

Natywny typ danych kolumn w magazynie danych nie ma znaczenia; tak długo, jak dostawca może obsługiwać konwersję danych, dostarczy dane w formacie ciągu. Jeśli dostawca nie obsługuje konwersji z natywnego typu danych na ciąg (który nie jest typowy), wywołanie żądania zwróci wartość sukcesu DB_S_ERRORSOCCURED, a stan odpowiedniej kolumny wskazuje na problem z konwersją DBSTATUS_E_CANTCONVERTVALUE.

Użyj metod `CDynamicStringAccessor`, aby uzyskać informacje o kolumnie. Te informacje o kolumnie służą do dynamicznego tworzenia akcesora w czasie wykonywania.

Informacje o kolumnie są przechowywane w buforze utworzonym i zarządzanym przez tę klasę. Pobierz dane z buforu za pomocą polecenia [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)lub Zapisz je w buforze przy użyciu polecenia [SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).

Aby zapoznać się z omówieniem i przykładami dotyczącymi korzystania z klas akcesorów dynamicznych, zobacz [Używanie dynamicznych metod dostępu](../../data/oledb/using-dynamic-accessors.md).

## <a name="cdynamicstringaccessorgetstring"></a><a name="getstring"></a>CDynamicStringAccessor:: GetString

Pobiera dane określonego kolumny jako ciąg.

### <a name="syntax"></a>Składnia

```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();

BaseType* GetString(const CHAR* pColumnName) const throw();

BaseType* GetString(const WCHAR* pColumnName) const throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
podczas Numer kolumny. Numery kolumn zaczynają się od 1. Wartość 0 oznacza kolumnę zakładki (jeśli istnieje).

*pColumnName*<br/>
podczas Wskaźnik do ciągu znaków, który zawiera nazwę kolumny.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wartości ciągu pobranej z określonej kolumny. Wartość jest typu `BaseType`, która będzie równa **char** lub **WCHAR** , w zależności od tego, czy _UNICODE jest zdefiniowany, czy nie. Zwraca wartość NULL, jeśli nie można odnaleźć określonej kolumny.

### <a name="remarks"></a>Uwagi

Drugi formularz przesłonięcia przyjmuje nazwę kolumny jako ciąg ANSI. Trzeci formularz przesłonięcia przyjmuje nazwę kolumny jako ciąg Unicode.

## <a name="cdynamicstringaccessorsetstring"></a><a name="setstring"></a>CDynamicStringAccessor:: SetString

Ustawia dane określonego kolumny jako ciąg.

### <a name="syntax"></a>Składnia

```cpp
HRESULT SetString(DBORDINAL nColumn,
   BaseType* data) throw();

HRESULT SetString(const CHAR* pColumnName,
   BaseType* data) throw();

HRESULT SetString(const WCHAR* pColumnName,
   BaseType* data) throw();
```

#### <a name="parameters"></a>Parametry

*nColumn*<br/>
podczas Numer kolumny. Numery kolumn zaczynają się od 1. Wartość specjalna 0 odwołuje się do kolumny zakładki (jeśli istnieje).

*pColumnName*<br/>
podczas Wskaźnik do ciągu znaków, który zawiera nazwę kolumny.

*Data*<br/>
podczas Wskaźnik do danych ciągu, który ma zostać zapisany w określonej kolumnie.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do wartości ciągu, do której ma zostać ustawiona określona kolumna. Wartość jest typu `BaseType`, która będzie równa **char** lub **WCHAR** , w zależności od tego, czy _UNICODE jest zdefiniowany, czy nie.

### <a name="remarks"></a>Uwagi

Drugi formularz przesłonięcia przyjmuje nazwę kolumny jako ciąg ANSI, a trzeci formularz przesłonięcia przyjmuje nazwę kolumny jako ciąg Unicode.

Jeśli _SECURE_ATL jest zdefiniowany jako mające wartość różną od zera, zostanie wygenerowany błąd potwierdzenia środowiska uruchomieniowego, jeśli ciąg *danych* wejściowych będzie dłuższy niż maksymalna dozwolona długość kolumny danych, której dotyczy odwołanie. W przeciwnym razie ciąg wejściowy zostanie obcięty, jeśli przekracza maksymalną dozwoloną długość.

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, klasa](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor, klasa](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA, klasa](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW, klasa](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor, klasa](../../data/oledb/cxmlaccessor-class.md)
