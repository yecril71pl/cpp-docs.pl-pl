---
title: Klasa CDBVariant
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
ms.openlocfilehash: 9bb70acb43f2e73ade86b753ebbb7949759ce88d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754601"
---
# <a name="cdbvariant-class"></a>Klasa CDBVariant

Reprezentuje typ danych wariantu dla klas ODBC MFC.

## <a name="syntax"></a>Składnia

```
class CDBVariant
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDBVariant::CDBVariant](#cdbvariant)|Konstruuje `CDBVariant` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDBVariant::Wyczyść](#clear)|Czyści `CDBVariant` obiekt.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDBVariant::m_dwType](#m_dwtype)|Zawiera typ danych aktualnie przechowywanej wartości. Wpisz polecenie `DWORD`.|

### <a name="public-union-members"></a>Członkowie Unii Publicznej

|Nazwa|Opis|
|----------|-----------------|
|[CDBVariant::m_boolVal](#m_boolval)|Zawiera wartość typu **BOOL**.|
|[CDBVariant::m_chVal](#m_chval)|Zawiera wartość typu **niepodpisanego char**.|
|[CDBVariant::m_dblVal](#m_dblval)|Zawiera wartość typu **double**.|
|[CDBVariant::m_fltVal](#m_fltval)|Zawiera wartość **typu float**.|
|[CDBVariant::m_iVal](#m_ival)|Zawiera wartość typu **krótkiego**.|
|[CDBVariant::m_lVal](#m_lval)|Zawiera wartość typu **long**.|
|[CDBVariant::m_pbinary](#m_pbinary)|Zawiera wskaźnik do obiektu `CLongBinary`typu .|
|[CDBVariant::m_pdate](#m_pdate)|Zawiera wskaźnik do obiektu typu **TIMESTAMP_STRUCT**.|
|[CDBVariant::m_pstring](#m_pstring)|Zawiera wskaźnik do obiektu `CString`typu .|
|[CDBVariant::m_pstringA](#m_pstringa)|Przechowuje wskaźnik do obiektu ASCII [CString.](../../atl-mfc-shared/reference/cstringt-class.md)|
|[CDBVariant::m_pstringW](#m_pstringw)|Przechowuje wskaźnik do szerokiego [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu.|

## <a name="remarks"></a>Uwagi

`CDBVariant`nie ma klasy podstawowej.

`CDBVariant`jest podobny do [COleVariant;](../../mfc/reference/colevariant-class.md) jednak `CDBVariant` nie używa OLE. `CDBVariant`umożliwia przechowywanie wartości bez martwienia się o typ danych wartości. `CDBVariant`śledzi typ danych bieżącej wartości, która jest przechowywana w unii.

Klasa [CRecordset](../../mfc/reference/crecordset-class.md) `CDBVariant` wykorzystuje obiekty w `GetFieldValue`trzech `GetBookmark`funkcjach członkowskich: , , i `SetBookmark`. Na przykład `GetFieldValue` umożliwia dynamiczne pobieranie danych w kolumnie. Ponieważ typ danych kolumny może nie być znany `GetFieldValue` w `CDBVariant` czasie wykonywania, używa obiektu do przechowywania danych kolumny.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CDBVariant`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="cdbvariantcdbvariant"></a><a name="cdbvariant"></a>CDBVariant::CDBVariant

Tworzy obiekt `CDBVariant` NULL.

```
CDBVariant();
```

### <a name="remarks"></a>Uwagi

Ustawia [element](#m_dwtype) członkowski m_dwType danych na DBVT_NULL.

## <a name="cdbvariantclear"></a><a name="clear"></a>CDBVariant::Wyczyść

Wywołanie tej funkcji `CDBVariant` elementu członkowskiego, aby wyczyścić obiekt.

```cpp
void Clear();
```

### <a name="remarks"></a>Uwagi

Jeśli wartość elementu członkowskiego [m_dwType](#m_dwtype) danych jest DBVT_DATE, DBVT_STRING lub DBVT_BINARY, `Clear` zwalnia pamięć skojarzoną z elementem członkowskim wskaźnika unii. `Clear`zestawy `m_dwType` do DBVT_NULL.

Destruktor `CDBVariant` wywołuje `Clear`.

## <a name="cdbvariantm_boolval"></a><a name="m_boolval"></a>CDBVariant::m_boolVal

Przechowuje wartość typu BOOL.

### <a name="remarks"></a>Uwagi

Element `m_boolVal` członkowski danych należy do unii. Przed wejściem `m_boolVal`do programu najpierw sprawdź wartość [cdbvariant::m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_BOOL, a następnie `m_boolVal` będzie zawierać prawidłową wartość; w przeciwnym `m_boolVal` razie dostęp przyniesie niewiarygodne wyniki.

## <a name="cdbvariantm_chval"></a><a name="m_chval"></a>CDBVariant::m_chVal

Przechowuje wartość typu **niepodpisanego char**.

### <a name="remarks"></a>Uwagi

Element `m_chVal` członkowski danych należy do unii. Przed wejściem `m_chVal`do programu najpierw sprawdź wartość [cdbvariant::m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_UCHAR, a następnie `m_chVal` zawiera prawidłową wartość; w przeciwnym `m_chVal` razie dostęp przyniesie niewiarygodne wyniki.

## <a name="cdbvariantm_dblval"></a><a name="m_dblval"></a>CDBVariant::m_dblVal

Przechowuje wartość typu **double**.

### <a name="remarks"></a>Uwagi

Element `m_dblVal` członkowski danych należy do unii. Przed wejściem `m_dblVal`do programu najpierw sprawdź wartość [cdbvariant::m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_DOUBLE, a następnie `m_dblVal` zawiera prawidłową wartość; w przeciwnym `m_dblVal` razie dostęp przyniesie niewiarygodne wyniki.

## <a name="cdbvariantm_dwtype"></a><a name="m_dwtype"></a>CDBVariant::m_dwType

Ten element członkowski danych zawiera typ danych dla `CDBVariant` wartości, która jest obecnie przechowywana w obiekcie elementu członkowskiego danych unii.

### <a name="remarks"></a>Uwagi

Przed wejściem do tej unii, `m_dwType` należy sprawdzić wartość w celu określenia, który element członkowski danych unii, aby uzyskać dostęp. W poniższej tabeli `m_dwType` wymieniono możliwe wartości dla i odpowiedniego elementu członkowskiego danych unii.

|M_dwtype|Unijny element członkowski ds.|
|---------------|-----------------------|
|DBVT_NULL|Żaden członek związku nie jest ważny dla dostępu.|
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

## <a name="cdbvariantm_fltval"></a><a name="m_fltval"></a>CDBVariant::m_fltVal

Przechowuje wartość **typu float**.

### <a name="remarks"></a>Uwagi

Element `m_fltVal` członkowski danych należy do unii. Przed wejściem `m_fltVal`do programu najpierw sprawdź wartość [cdbvariant::m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_SINGLE, a następnie `m_fltVal` zawiera prawidłową wartość; w przeciwnym `m_fltVal` razie dostęp przyniesie niewiarygodne wyniki.

## <a name="cdbvariantm_ival"></a><a name="m_ival"></a>CDBVariant::m_iVal

Przechowuje wartość typu **krótki**.

### <a name="remarks"></a>Uwagi

Element `m_iVal` członkowski danych należy do unii. Przed wejściem `m_iVal`do programu najpierw sprawdź wartość [cdbvariant::m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_SHORT, a następnie `m_iVal` zawiera prawidłową wartość; w przeciwnym `m_iVal` razie dostęp przyniesie niewiarygodne wyniki.

## <a name="cdbvariantm_lval"></a><a name="m_lval"></a>CDBVariant::m_lVal

Przechowuje wartość typu **long**.

### <a name="remarks"></a>Uwagi

Element `m_lVal` członkowski danych należy do unii. Przed wejściem `m_lVal`do programu najpierw sprawdź wartość [cdbvariant::m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_LONG, a następnie `m_lVal` zawiera prawidłową wartość; w przeciwnym `m_lVal` razie dostęp przyniesie niewiarygodne wyniki.

## <a name="cdbvariantm_pbinary"></a><a name="m_pbinary"></a>CDBVariant::m_pbinary

Przechowuje wskaźnik do obiektu typu [CLongBinary](../../mfc/reference/clongbinary-class.md).

### <a name="remarks"></a>Uwagi

Element `m_pbinary` członkowski danych należy do unii. Przed wejściem `m_pbinary`do programu najpierw sprawdź wartość [cdbvariant::m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_BINARY, a następnie `m_pbinary` zawiera prawidłowy wskaźnik; w przeciwnym `m_pbinary` razie dostęp przyniesie niewiarygodne wyniki.

## <a name="cdbvariantm_pdate"></a><a name="m_pdate"></a>CDBVariant::m_pdate

Przechowuje wskaźnik do obiektu typu TIMESTAMP_STRUCT.

### <a name="remarks"></a>Uwagi

Element `m_pdate` członkowski danych należy do unii. Przed wejściem `m_pdate`do programu najpierw sprawdź wartość [cdbvariant::m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_DATE, a następnie `m_pdate` zawiera prawidłowy wskaźnik; w przeciwnym `m_pdate` razie dostęp przyniesie niewiarygodne wyniki.

Aby uzyskać więcej informacji na temat TIMESTAMP_STRUCT typu danych, zobacz temat [Typy danych C](/sql/odbc/reference/appendixes/c-data-types) w dodatku D *odwołania programisty ODBC* w zestaw Windows SDK.

## <a name="cdbvariantm_pstring"></a><a name="m_pstring"></a>CDBVariant::m_pstring

Przechowuje wskaźnik do obiektu typu [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

Element `m_pstring` członkowski danych należy do unii. Przed wejściem `m_pstring`do programu najpierw sprawdź wartość [cdbvariant::m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_STRING, a następnie `m_pstring` zawiera prawidłowy wskaźnik; w przeciwnym `m_pstring` razie dostęp przyniesie niewiarygodne wyniki.

## <a name="cdbvariantm_pstringa"></a><a name="m_pstringa"></a>CDBVariant::m_pstringA

Przechowuje wskaźnik do obiektu ASCII [CString.](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>Uwagi

Element `m_pstringA` członkowski danych należy do unii. Przed wejściem `m_pstringA`do programu najpierw sprawdź wartość [cdbvariant::m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_ASTRING, a następnie `m_pstringA` zawiera prawidłowy wskaźnik; w przeciwnym `m_pstringA` razie dostęp przyniesie niewiarygodne wyniki.

## <a name="cdbvariantm_pstringw"></a><a name="m_pstringw"></a>CDBVariant::m_pstringW

Przechowuje wskaźnik do szerokiego [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu.

### <a name="remarks"></a>Uwagi

Element `m_pstringW` członkowski danych należy do unii. Przed wejściem `m_pstringW`do programu najpierw sprawdź wartość [cdbvariant::m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_WSTRING, a następnie `m_pstringW` zawiera prawidłowy wskaźnik; w przeciwnym `m_pstringW` razie dostęp przyniesie niewiarygodne wyniki.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
