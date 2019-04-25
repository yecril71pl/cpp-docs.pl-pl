---
title: Klasa CXMLAccessor
ms.date: 11/04/2016
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
- ATL.CXMLAccessor.GetXMLColumnData
- CXMLAccessor::GetXMLColumnData
- CXMLAccessor.GetXMLColumnData
- ATL::CXMLAccessor::GetXMLColumnData
- GetXMLColumnData
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
helpviewer_keywords:
- CXMLAccessor class
- GetXMLColumnData method
- GetXMLRowData method
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
ms.openlocfilehash: 85fddb9b77cfc089b2236f2ff82944fec6ef9632
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176073"
---
# <a name="cxmlaccessor-class"></a>Klasa CXMLAccessor

Umożliwia dostęp do źródła danych jako dane ciągu, jeśli masz nie znajomości schematu magazynu danych (wewnętrzna struktura).

## <a name="syntax"></a>Składnia

```cpp
class CXMLAccessor : public CDynamicStringAccessorW
```

## <a name="requirements"></a>Wymagania

**Nagłówek**: atldbcli.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[GetXMLColumnData](#getxmlcolumndata)|Pobiera informacje o kolumnach.|
|[GetXMLRowData](#getxmlrowdata)|Pobiera całą zawartość tabeli według wierszy.|

## <a name="remarks"></a>Uwagi

Jednak `CXMLAccessor` różni się od `CDynamicStringAccessorW` , konwertuje wszystkie dane używane z magazynu danych jako danych (oznakowany) w formacie XML. Jest to szczególnie przydatne dla danych wyjściowych do stron sieci Web XML-aware. Nazwy tagów XML w możliwie najlepszy sposób będą zgodne nazwy kolumn w magazynie danych.

Użyj `CDynamicAccessor` metody, aby uzyskać informacje o kolumnach. Informacje o kolumnie umożliwia dynamiczne tworzenie metody dostępu w czasie wykonywania.

Informacje o kolumnach są przechowywane w buforze tworzone i zarządzane przez tę klasę. Uzyskaj informacje przy użyciu kolumny [getxmlcolumndata —](#getxmlcolumndata) lub uzyskania kolumny danych według wierszy przy użyciu [getxmlrowdata —](#getxmlrowdata).

## <a name="example"></a>Przykład

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="getxmlcolumndata"></a> CXMLAccessor::GetXMLColumnData

Pobiera informacje o typie kolumny tabeli jako ciąg w formacie XML danych, według kolumny.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>Parametry

*strOutput*<br/>
[out] Odwołanie do buforu ciągu zawierający informacje o typie kolumny mają zostać pobrane. Ten ciąg jest formatowana przy użyciu nazwy tagów XML i być zgodne z nazwami kolumn magazynu danych.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Poniżej przedstawiono, jak informacje o typie kolumny jest sformatowany w języku XML. `type` Określa typ danych kolumny. Należy pamiętać, że typy danych są oparte na typach danych OLE DB, wyklucza te bazy danych, do którego uzyskiwany jest dostęp.

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="getxmlrowdata"></a> CXMLAccessor::GetXMLRowData

Pobiera całą zawartość tabeli jako dane ciągu w formacie XML, po wierszu.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>Parametry

*strOutput*<br/>
[out] Odwołanie do buforu, zawierająca dane tabeli, które mają zostać pobrane. Dane są sformatowane jako ciąg danych przy użyciu nazwy tagów XML i być zgodne z nazwami kolumn magazynu danych.

*bAppend*<br/>
[in] Wartość logiczna określająca, czy dołączyć ciąg na końcu danych wyjściowych.

### <a name="return-value"></a>Wartość zwracana

Jedna z wartości HRESULT standardowych.

### <a name="remarks"></a>Uwagi

Na poniższym obrazie przedstawiono sposób formatowania danych wierszy w formacie XML. `DATA` poniżej reprezentuje wiersz danych. Użyj opcji move metody, aby przejść do żądanego wiersza.

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, klasa](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor, klasa](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA, klasa](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW, klasa](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor, klasa](../../data/oledb/cmanualaccessor-class.md)