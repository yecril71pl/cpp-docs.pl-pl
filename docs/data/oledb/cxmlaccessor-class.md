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
ms.openlocfilehash: f25fb3635f70ee9a0e38ddcdbcf373fe6b1b84c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211045"
---
# <a name="cxmlaccessor-class"></a>Klasa CXMLAccessor

Pozwala uzyskać dostęp do źródeł danych jako dane ciągu, gdy nie masz informacji o schemacie magazynu danych (struktura bazowa).

## <a name="syntax"></a>Składnia

```cpp
class CXMLAccessor : public CDynamicStringAccessorW
```

## <a name="requirements"></a>Wymagania

**Nagłówek**: atldbcli. h

## <a name="members"></a>Members

### <a name="methods"></a>Metody

|||
|-|-|
|[GetXMLColumnData](#getxmlcolumndata)|Pobiera informacje o kolumnie.|
|[GetXMLRowData](#getxmlrowdata)|Pobiera całą zawartość tabeli według wierszy.|

## <a name="remarks"></a>Uwagi

Jednak `CXMLAccessor` różni się od `CDynamicStringAccessorW` w tym, że konwertuje wszystkie dane, do których uzyskano dostęp z magazynu danych jako dane sformatowane w formacie XML (oznakowane). Jest to szczególnie przydatne w przypadku danych wyjściowych na stronach sieci Web obsługujących język XML. Nazwy tagów XML będą zgodne z nazwami kolumn magazynu danych tak blisko jak to możliwe.

Użyj metod `CDynamicAccessor`, aby uzyskać informacje o kolumnie. Te informacje o kolumnie służą do dynamicznego tworzenia akcesora w czasie wykonywania.

Informacje o kolumnie są przechowywane w buforze utworzonym i zarządzanym przez tę klasę. Uzyskiwanie informacji o kolumnach przy użyciu [GetXMLColumnData](#getxmlcolumndata) lub uzyskiwanie danych z kolumn przez wiersze przy użyciu [GetXMLRowData](#getxmlrowdata).

## <a name="example"></a>Przykład

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="cxmlaccessorgetxmlcolumndata"></a><a name="getxmlcolumndata"></a>CXMLAccessor:: GetXMLColumnData

Pobiera informacje o typie kolumny tabeli jako dane ciągu sformatowane w formacie XML według kolumny.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>Parametry

*strOutput*<br/>
określoną Odwołanie do buforu ciągu zawierającego informacje o typie kolumny do pobrania. Ciąg jest sformatowany przy użyciu nazw tagów XML, które pasują do nazw kolumn magazynu danych.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Poniżej przedstawiono sposób formatowania informacji o typie kolumny w formacie XML. `type` określa typ danych kolumny. Należy pamiętać, że typy danych są oparte na typach danych OLE DB, a nie w przypadku uzyskiwania dostępu do bazy danych.

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="cxmlaccessorgetxmlrowdata"></a><a name="getxmlrowdata"></a>CXMLAccessor:: GetXMLRowData

Pobiera całą zawartość tabeli jako dane ciągu w formacie XML według wiersza.

### <a name="syntax"></a>Składnia

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>Parametry

*strOutput*<br/>
określoną Odwołanie do buforu zawierającego dane tabeli do pobrania. Dane są formatowane jako dane ciągu z nazwami tagów XML, które pasują do nazw kolumn magazynu danych.

*bAppend*<br/>
podczas Wartość logiczna określająca, czy dołączać ciąg na końcu danych wyjściowych.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Poniżej pokazano, jak dane wiersza są formatowane w formacie XML. `DATA` poniżej reprezentuje dane wiersza. Użyj metody Move, aby przejść do żądanego wiersza.

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, klasa](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor, klasa](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA, klasa](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW, klasa](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor, klasa](../../data/oledb/cmanualaccessor-class.md)
