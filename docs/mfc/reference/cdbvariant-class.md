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
ms.openlocfilehash: 45a478a5ca6cfb4d9b976a29eae2ae7d98fdd6ee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223086"
---
# <a name="cdbvariant-class"></a>Klasa CDBVariant

Reprezentuje typ danych Variant dla klas MFC ODBC.

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
|[CDBVariant:: Clear](#clear)|Czyści `CDBVariant` obiekt.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CDBVariant:: m_dwType](#m_dwtype)|Zawiera typ danych aktualnie przechowywanej wartości. Wpisz `DWORD`.|

### <a name="public-union-members"></a>Członkowie Unii publicznej

|Nazwa|Opis|
|----------|-----------------|
|[CDBVariant:: m_boolVal](#m_boolval)|Zawiera wartość typu **bool**.|
|[CDBVariant:: m_chVal](#m_chval)|Zawiera wartość typu **`unsigned char`** .|
|[CDBVariant:: m_dblVal](#m_dblval)|Zawiera wartość typu **`double`** .|
|[CDBVariant:: m_fltVal](#m_fltval)|Zawiera wartość typu **`float`** .|
|[CDBVariant:: m_iVal](#m_ival)|Zawiera wartość typu **`short`** .|
|[CDBVariant:: m_lVal](#m_lval)|Zawiera wartość typu **`long`** .|
|[CDBVariant:: m_pbinary](#m_pbinary)|Zawiera wskaźnik do obiektu typu `CLongBinary` .|
|[CDBVariant:: m_pdate](#m_pdate)|Zawiera wskaźnik do obiektu typu **TIMESTAMP_STRUCT**.|
|[CDBVariant:: m_pstring](#m_pstring)|Zawiera wskaźnik do obiektu typu `CString` .|
|[CDBVariant:: m_pstringA](#m_pstringa)|Przechowuje wskaźnik do obiektu [CSTRING](../../atl-mfc-shared/reference/cstringt-class.md) ASCII.|
|[CDBVariant:: m_pstringW](#m_pstringw)|Przechowuje wskaźnik do szerokiego obiektu [CString](../../atl-mfc-shared/reference/cstringt-class.md) .|

## <a name="remarks"></a>Uwagi

`CDBVariant`nie ma klasy bazowej.

`CDBVariant`jest podobny do [COleVariant](../../mfc/reference/colevariant-class.md); nie `CDBVariant` używa jednak OLE. `CDBVariant`umożliwia przechowywanie wartości bez obaw o typ danych wartości. `CDBVariant`śledzi typ danych bieżącej wartości, który jest przechowywany w Unii.

Klasa [CRecordset](../../mfc/reference/crecordset-class.md) wykorzystuje `CDBVariant` obiekty w trzech funkcjach członkowskich: `GetFieldValue` , `GetBookmark` , i `SetBookmark` . Na przykład program `GetFieldValue` umożliwia dynamiczne pobieranie danych w kolumnie. Ponieważ typ danych kolumny może nie być znany w czasie wykonywania, program `GetFieldValue` używa `CDBVariant` obiektu do przechowywania danych tej kolumny.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CDBVariant`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="cdbvariantcdbvariant"></a><a name="cdbvariant"></a>CDBVariant::CDBVariant

Tworzy obiekt o wartości NULL `CDBVariant` .

```
CDBVariant();
```

### <a name="remarks"></a>Uwagi

Ustawia element członkowski danych [m_dwType](#m_dwtype) na DBVT_NULL.

## <a name="cdbvariantclear"></a><a name="clear"></a>CDBVariant:: Clear

Wywołaj tę funkcję elementu członkowskiego, aby wyczyścić `CDBVariant` obiekt.

```cpp
void Clear();
```

### <a name="remarks"></a>Uwagi

Jeśli wartość [m_dwType](#m_dwtype) elementu członkowskiego danych jest DBVT_DATE, DBVT_STRING lub DBVT_BINARY, `Clear` zwalnia pamięć skojarzoną z elementem członkowskim wskaźnika Union. `Clear`ustawia `m_dwType` DBVT_NULL.

`CDBVariant`Destruktor wywołuje `Clear` .

## <a name="cdbvariantm_boolval"></a><a name="m_boolval"></a>CDBVariant:: m_boolVal

Przechowuje wartość typu BOOL.

### <a name="remarks"></a>Uwagi

`m_boolVal`Element członkowski danych należy do Unii. Przed uzyskaniem dostępu `m_boolVal` należy najpierw sprawdzić wartość [CDBVariant:: m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_BOOL, `m_boolVal` będzie zawierać prawidłową wartość. w przeciwnym razie dostęp do nich `m_boolVal` spowoduje powstanie wiarygodnych wyników.

## <a name="cdbvariantm_chval"></a><a name="m_chval"></a>CDBVariant:: m_chVal

Przechowuje wartość typu **`unsigned char`** .

### <a name="remarks"></a>Uwagi

`m_chVal`Element członkowski danych należy do Unii. Przed uzyskaniem dostępu `m_chVal` należy najpierw sprawdzić wartość [CDBVariant:: m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_UCHAR, `m_chVal` zawiera prawidłową wartość. w przeciwnym razie uzyskanie dostępu `m_chVal` spowoduje niezawodne wyniki.

## <a name="cdbvariantm_dblval"></a><a name="m_dblval"></a>CDBVariant:: m_dblVal

Przechowuje wartość typu **`double`** .

### <a name="remarks"></a>Uwagi

`m_dblVal`Element członkowski danych należy do Unii. Przed uzyskaniem dostępu `m_dblVal` należy najpierw sprawdzić wartość [CDBVariant:: m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_DOUBLE, `m_dblVal` zawiera prawidłową wartość. w przeciwnym razie uzyskanie dostępu `m_dblVal` spowoduje niezawodne wyniki.

## <a name="cdbvariantm_dwtype"></a><a name="m_dwtype"></a>CDBVariant:: m_dwType

Ten element członkowski danych zawiera typ danych dla wartości, która jest obecnie przechowywana w `CDBVariant` elemencie członkowskim danych Union obiektu.

### <a name="remarks"></a>Uwagi

Przed uzyskaniem dostępu do tego związku należy sprawdzić wartość `m_dwType` w polu, aby określić, który element członkowski danych związku ma uzyskać dostęp. Poniższa tabela zawiera listę możliwych wartości dla `m_dwType` i odpowiedniego elementu członkowskiego danych związku.

|m_dwType|Element członkowski danych Union|
|---------------|-----------------------|
|DBVT_NULL|Żaden członek Unii nie jest prawidłowy dla dostępu.|
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

## <a name="cdbvariantm_fltval"></a><a name="m_fltval"></a>CDBVariant:: m_fltVal

Przechowuje wartość typu **`float`** .

### <a name="remarks"></a>Uwagi

`m_fltVal`Element członkowski danych należy do Unii. Przed uzyskaniem dostępu `m_fltVal` należy najpierw sprawdzić wartość [CDBVariant:: m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_SINGLE, `m_fltVal` zawiera prawidłową wartość. w przeciwnym razie uzyskanie dostępu `m_fltVal` spowoduje niezawodne wyniki.

## <a name="cdbvariantm_ival"></a><a name="m_ival"></a>CDBVariant:: m_iVal

Przechowuje wartość typu **`short`** .

### <a name="remarks"></a>Uwagi

`m_iVal`Element członkowski danych należy do Unii. Przed uzyskaniem dostępu `m_iVal` należy najpierw sprawdzić wartość [CDBVariant:: m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_SHORT, `m_iVal` zawiera prawidłową wartość. w przeciwnym razie uzyskanie dostępu `m_iVal` spowoduje niezawodne wyniki.

## <a name="cdbvariantm_lval"></a><a name="m_lval"></a>CDBVariant:: m_lVal

Przechowuje wartość typu **`long`** .

### <a name="remarks"></a>Uwagi

`m_lVal`Element członkowski danych należy do Unii. Przed uzyskaniem dostępu `m_lVal` należy najpierw sprawdzić wartość [CDBVariant:: m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_LONG, `m_lVal` zawiera prawidłową wartość. w przeciwnym razie uzyskanie dostępu `m_lVal` spowoduje niezawodne wyniki.

## <a name="cdbvariantm_pbinary"></a><a name="m_pbinary"></a>CDBVariant:: m_pbinary

Przechowuje wskaźnik do obiektu typu [CLongBinary](../../mfc/reference/clongbinary-class.md).

### <a name="remarks"></a>Uwagi

`m_pbinary`Element członkowski danych należy do Unii. Przed uzyskaniem dostępu `m_pbinary` należy najpierw sprawdzić wartość [CDBVariant:: m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_BINARY, `m_pbinary` zawiera prawidłowy wskaźnik; w przeciwnym razie uzyskanie dostępu `m_pbinary` spowoduje uzyskanie wiarygodnych wyników.

## <a name="cdbvariantm_pdate"></a><a name="m_pdate"></a>CDBVariant:: m_pdate

Przechowuje wskaźnik do obiektu typu TIMESTAMP_STRUCT.

### <a name="remarks"></a>Uwagi

`m_pdate`Element członkowski danych należy do Unii. Przed uzyskaniem dostępu `m_pdate` należy najpierw sprawdzić wartość [CDBVariant:: m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_DATE, `m_pdate` zawiera prawidłowy wskaźnik; w przeciwnym razie uzyskanie dostępu `m_pdate` spowoduje uzyskanie wiarygodnych wyników.

Aby uzyskać więcej informacji na temat typu danych TIMESTAMP_STRUCT, zobacz temat [typy danych](/sql/odbc/reference/appendixes/c-data-types) w temacie C w dodatku D *odwołania ODBC programmer's* w Windows SDK.

## <a name="cdbvariantm_pstring"></a><a name="m_pstring"></a>CDBVariant:: m_pstring

Przechowuje wskaźnik do obiektu typu [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Uwagi

`m_pstring`Element członkowski danych należy do Unii. Przed uzyskaniem dostępu `m_pstring` należy najpierw sprawdzić wartość [CDBVariant:: m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_STRING, `m_pstring` zawiera prawidłowy wskaźnik; w przeciwnym razie uzyskanie dostępu `m_pstring` spowoduje uzyskanie wiarygodnych wyników.

## <a name="cdbvariantm_pstringa"></a><a name="m_pstringa"></a>CDBVariant:: m_pstringA

Przechowuje wskaźnik do obiektu [CSTRING](../../atl-mfc-shared/reference/cstringt-class.md) ASCII.

### <a name="remarks"></a>Uwagi

`m_pstringA`Element członkowski danych należy do Unii. Przed uzyskaniem dostępu `m_pstringA` należy najpierw sprawdzić wartość [CDBVariant:: m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_ASTRING, `m_pstringA` zawiera prawidłowy wskaźnik; w przeciwnym razie uzyskanie dostępu `m_pstringA` spowoduje uzyskanie wiarygodnych wyników.

## <a name="cdbvariantm_pstringw"></a><a name="m_pstringw"></a>CDBVariant:: m_pstringW

Przechowuje wskaźnik do szerokiego obiektu [CString](../../atl-mfc-shared/reference/cstringt-class.md) .

### <a name="remarks"></a>Uwagi

`m_pstringW`Element członkowski danych należy do Unii. Przed uzyskaniem dostępu `m_pstringW` należy najpierw sprawdzić wartość [CDBVariant:: m_dwType](#m_dwtype). Jeśli `m_dwType` jest ustawiona na DBVT_WSTRING, `m_pstringW` zawiera prawidłowy wskaźnik; w przeciwnym razie uzyskanie dostępu `m_pstringW` spowoduje uzyskanie wiarygodnych wyników.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
