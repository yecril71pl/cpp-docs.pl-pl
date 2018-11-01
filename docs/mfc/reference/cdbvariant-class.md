---
title: Cdbvariant — klasa
ms.date: 11/04/2016
f1_keywords:
- CDBVariant
- AFXDB/CDBVariant
- AFXDB/CDBVariant::CDBVariant
- AFXDB/CDBVariant::Clear
- AFXDB/CDBVariant::m_dwType
- AFXDB/CDBVariant::m_boolVal
- AFXDB/CDBVariant::m_chVal
- AFXDB/CDBVariant::m_dblVal
- AFXDB/CDBVariant::m_fltVal
- AFXDB/CDBVariant::m_iVal
- AFXDB/CDBVariant::m_lVal
- AFXDB/CDBVariant::m_pbinary
- AFXDB/CDBVariant::m_pdate
- AFXDB/CDBVariant::m_pstring
- AFXDB/CDBVariant::m_pstringA
- AFXDB/CDBVariant::m_pstringW
helpviewer_keywords:
- CDBVariant [MFC], CDBVariant
- CDBVariant [MFC], Clear
- CDBVariant [MFC], m_dwType
- CDBVariant [MFC], m_boolVal
- CDBVariant [MFC], m_chVal
- CDBVariant [MFC], m_dblVal
- CDBVariant [MFC], m_fltVal
- CDBVariant [MFC], m_iVal
- CDBVariant [MFC], m_lVal
- CDBVariant [MFC], m_pbinary
- CDBVariant [MFC], m_pdate
- CDBVariant [MFC], m_pstring
- CDBVariant [MFC], m_pstringA
- CDBVariant [MFC], m_pstringW
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
ms.openlocfilehash: 2a600aa893ae86abebb4146eda4864e69da3c35c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485309"
---
# <a name="cdbvariant-class"></a>Cdbvariant — klasa

Reprezentuje typ danych Wariant dla klas MFC ODBC.

## <a name="syntax"></a>Składnia

```
class CDBVariant
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDBVariant::CDBVariant](#cdbvariant)|Konstruuje `CDBVariant` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDBVariant::Clear](#clear)|Czyści `CDBVariant` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDBVariant::m_dwType](#m_dwtype)|Zawiera typ danych obecnie przechowywanej wartości. Typ `DWORD`.|

### <a name="public-union-members"></a>Publicznych składowych Unii

|Nazwa|Opis|
|----------|-----------------|
|[CDBVariant::m_boolVal](#m_boolval)|Zawiera wartość typu **BOOL**.|
|[CDBVariant::m_chVal](#m_chval)|Zawiera wartość typu **unsigned char**.|
|[CDBVariant::m_dblVal](#m_dblval)|Zawiera wartość typu **double**.|
|[CDBVariant::m_fltVal](#m_fltval)|Zawiera wartość typu **float**.|
|[CDBVariant::m_iVal](#m_ival)|Zawiera wartość typu **krótki**.|
|[CDBVariant::m_lVal](#m_lval)|Zawiera wartość typu **długie**.|
|[CDBVariant::m_pbinary](#m_pbinary)|Zawiera wskaźnik do obiektu typu `CLongBinary`.|
|[CDBVariant::m_pdate](#m_pdate)|Zawiera wskaźnik do obiektu typu **TIMESTAMP_STRUCT**.|
|[CDBVariant::m_pstring](#m_pstring)|Zawiera wskaźnik do obiektu typu `CString`.|
|[CDBVariant::m_pstringA](#m_pstringa)|Przechowuje wskaźnik do ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu.|
|[CDBVariant::m_pstringW](#m_pstringw)|Przechowuje wskaźnik do całej [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu.|

## <a name="remarks"></a>Uwagi

`CDBVariant` nie ma klasy bazowej.

`CDBVariant` jest podobny do [COleVariant](../../mfc/reference/colevariant-class.md); jednak `CDBVariant` nie korzysta z OLE. `CDBVariant` Służy do przechowywania wartości bez martwienia się o typ danych wartości. `CDBVariant` śledzi bieżącą wartość przechowywaną w Unii typ danych.

Klasa [CRecordset](../../mfc/reference/crecordset-class.md) wykorzystuje `CDBVariant` obiektów w trzech funkcji elementów członkowskich: `GetFieldValue`, `GetBookmark`, i `SetBookmark`. Na przykład `GetFieldValue` umożliwia dynamicznie pobrać dane w kolumnie. Ponieważ typ danych kolumny nie może być znane w czasie wykonywania, `GetFieldValue` używa `CDBVariant` obiektu do przechowywania danych w kolumnie.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CDBVariant`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

##  <a name="cdbvariant"></a>  CDBVariant::CDBVariant

Tworzy wartość NULL `CDBVariant` obiektu.

```
CDBVariant();
```

### <a name="remarks"></a>Uwagi

Zestawy [m_dwType](#m_dwtype) do DBVT_NULL element członkowski danych.

##  <a name="clear"></a>  CDBVariant::Clear

Wywołaj tę funkcję elementu członkowskiego, aby wyczyścić `CDBVariant` obiektu.

```
void Clear();
```

### <a name="remarks"></a>Uwagi

Jeśli wartość [m_dwType](#m_dwtype) element członkowski danych jest DBVT_DATE, DBVT_STRING lub DBVT_BINARY, `Clear` zwalnia pamięć skojarzone z elementem złożenia wskaźnika. `Clear` Ustawia `m_dwType` do DBVT_NULL.

`CDBVariant` Wywołania destruktora `Clear`.

##  <a name="m_boolval"></a>  CDBVariant::m_boolVal

Przechowuje wartość typu wartość logiczna.

### <a name="remarks"></a>Uwagi

`m_boolVal` Element członkowski danych należy do Unii. Przed uzyskaniem dostępu do `m_boolVal`, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono DBVT_BOOL, następnie `m_boolVal` będzie zawierać prawidłową wartością; w przeciwnym razie uzyskiwania dostępu do `m_boolVal` da niewiarygodne wyniki.

##  <a name="m_chval"></a>  CDBVariant::m_chVal

Przechowuje wartość typu **unsigned char**.

### <a name="remarks"></a>Uwagi

`m_chVal` Element członkowski danych należy do Unii. Przed uzyskaniem dostępu do `m_chVal`, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono DBVT_UCHAR, następnie `m_chVal` zawiera prawidłową wartością; w przeciwnym razie uzyskiwania dostępu do `m_chVal` da niewiarygodne wyniki.

##  <a name="m_dblval"></a>  CDBVariant::m_dblVal

Przechowuje wartość typu **double**.

### <a name="remarks"></a>Uwagi

`m_dblVal` Element członkowski danych należy do Unii. Przed uzyskaniem dostępu do `m_dblVal`, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono DBVT_DOUBLE, następnie `m_dblVal` zawiera prawidłową wartością; w przeciwnym razie uzyskiwania dostępu do `m_dblVal` da niewiarygodne wyniki.

##  <a name="m_dwtype"></a>  CDBVariant::m_dwType

Ten element członkowski danych zawiera typ danych dla wartości, która znajduje się obecnie w `CDBVariant` obiektu element członkowski danych Unii.

### <a name="remarks"></a>Uwagi

Przed uzyskaniem dostępu do tej Unii, należy sprawdzić wartość `m_dwType` w celu ustalenia, która składowa danych Unii, dostęp do. Poniższa tabela zawiera listę możliwych wartości dla `m_dwType` i odpowiedni element członkowski danych Unii.

|m_dwType|Element członkowski danych Unii|
|---------------|-----------------------|
|DBVT_NULL|Nie składowa typu Unii jest prawidłowy dla dostępu.|
|DBVT_BOOL|[m_boolVal](#m_boolval)|
|DBVT_UCHAR|[m_chVal](#m_chval)|
|DBVT_SHORT|[m_iVal](#m_ival)|
|DBVT_LONG|[m_lVal](#m_lval)|
|DBVT_SINGLE|[m_fltVal](#m_fltval)|
|DBVT_DOUBLE|[m_dblVal](#m_dblval)|
|DBVT_DATE|[m_pdate](#m_pdate)|
|DBVT_STRING|[m_pstring](#m_pstring)|
|DBVT_BINARY|[m_pbinary](#m_pbinary)|
|DBVT_ASTRING|[m_pstringA](#m_pstringa)|
|DBVT_WSTRING|[m_pstringW](#m_pstringw)|

##  <a name="m_fltval"></a>  CDBVariant::m_fltVal

Przechowuje wartość typu **float**.

### <a name="remarks"></a>Uwagi

`m_fltVal` Element członkowski danych należy do Unii. Przed uzyskaniem dostępu do `m_fltVal`, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono DBVT_SINGLE, następnie `m_fltVal` zawiera prawidłową wartością; w przeciwnym razie uzyskiwania dostępu do `m_fltVal` da niewiarygodne wyniki.

##  <a name="m_ival"></a>  CDBVariant::m_iVal

Przechowuje wartość typu **krótki**.

### <a name="remarks"></a>Uwagi

`m_iVal` Element członkowski danych należy do Unii. Przed uzyskaniem dostępu do `m_iVal`, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono DBVT_SHORT, następnie `m_iVal` zawiera prawidłową wartością; w przeciwnym razie uzyskiwania dostępu do `m_iVal` da niewiarygodne wyniki.

##  <a name="m_lval"></a>  CDBVariant::m_lVal

Przechowuje wartość typu **długie**.

### <a name="remarks"></a>Uwagi

`m_lVal` Element członkowski danych należy do Unii. Przed uzyskaniem dostępu do `m_lVal`, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono DBVT_LONG, następnie `m_lVal` zawiera prawidłową wartością; w przeciwnym razie uzyskiwania dostępu do `m_lVal` da niewiarygodne wyniki.

##  <a name="m_pbinary"></a>  CDBVariant::m_pbinary

Przechowuje wskaźnik do obiektu typu [CLongBinary](../../mfc/reference/clongbinary-class.md).

### <a name="remarks"></a>Uwagi

`m_pbinary` Element członkowski danych należy do Unii. Przed uzyskaniem dostępu do `m_pbinary`, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono DBVT_BINARY, następnie `m_pbinary` zawiera nieprawidłowy wskaźnik; w przeciwnym razie uzyskiwania dostępu do `m_pbinary` da niewiarygodne wyniki.

##  <a name="m_pdate"></a>  CDBVariant::m_pdate

Przechowuje wskaźnik do obiektu typu TIMESTAMP_STRUCT.

### <a name="remarks"></a>Uwagi

`m_pdate` Element członkowski danych należy do Unii. Przed uzyskaniem dostępu do `m_pdate`, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono DBVT_DATE, następnie `m_pdate` zawiera nieprawidłowy wskaźnik; w przeciwnym razie uzyskiwania dostępu do `m_pdate` da niewiarygodne wyniki.

Aby uzyskać więcej informacji o typie danych TIMESTAMP_STRUCT, zobacz temat [typów danych języka C](/previous-versions/windows/desktop/ms714556) w dodatku D *odwołania programisty ODBC* w zestawie Windows SDK.

##  <a name="m_pstring"></a>  CDBVariant::m_pstring

Przechowuje wskaźnik do obiektu typu [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

`m_pstring` Element członkowski danych należy do Unii. Przed uzyskaniem dostępu do `m_pstring`, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono DBVT_STRING, następnie `m_pstring` zawiera nieprawidłowy wskaźnik; w przeciwnym razie uzyskiwania dostępu do `m_pstring` da niewiarygodne wyniki.

##  <a name="m_pstringa"></a>  CDBVariant::m_pstringA

Przechowuje wskaźnik do ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu.

### <a name="remarks"></a>Uwagi

`m_pstringA` Element członkowski danych należy do Unii. Przed uzyskaniem dostępu do `m_pstringA`, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono DBVT_ASTRING, następnie `m_pstringA` zawiera nieprawidłowy wskaźnik; w przeciwnym razie uzyskiwania dostępu do `m_pstringA` da niewiarygodne wyniki.

##  <a name="m_pstringw"></a>  CDBVariant::m_pstringW

Przechowuje wskaźnik do całej [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu.

### <a name="remarks"></a>Uwagi

`m_pstringW` Element członkowski danych należy do Unii. Przed uzyskaniem dostępu do `m_pstringW`, najpierw należy sprawdzić wartość [CDBVariant::m_dwType](#m_dwtype). Jeśli `m_dwType` ustawiono DBVT_WSTRING, następnie `m_pstringW` zawiera nieprawidłowy wskaźnik; w przeciwnym razie uzyskiwania dostępu do `m_pstringW` da niewiarygodne wyniki.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
