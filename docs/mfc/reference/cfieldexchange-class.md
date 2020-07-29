---
title: Klasa CFieldExchange
ms.date: 11/04/2016
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
ms.openlocfilehash: d10bfc436297a5f861f17843007347dcef9e58ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212478"
---
# <a name="cfieldexchange-class"></a>Klasa CFieldExchange

Obsługuje procedury wymiany pól rekordów (RFX) i wymiany zbiorczych pól rekordów (bulk RFX) używanych przez klasy baz danych.

## <a name="syntax"></a>Składnia

```
class CFieldExchange
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFieldExchange:: IsFieldType](#isfieldtype)|Zwraca wartość różną od zera, jeśli bieżąca operacja jest odpowiednia dla typu aktualizowanego pola.|
|[CFieldExchange:: SetFieldType](#setfieldtype)|Określa typ składowej danych zestawu rekordów — kolumny lub parametru — reprezentowane przez wszystkie następujące wywołania funkcji RFX do momentu następnego wywołania metody `SetFieldType` .|

## <a name="remarks"></a>Uwagi

`CFieldExchange`nie ma klasy bazowej.

Użyj tej klasy, jeśli piszesz procedury wymiany danych dla niestandardowych typów danych lub podczas wdrażania pobierania wierszy zbiorczych; w przeciwnym razie nie będziesz bezpośrednio używać tej klasy. RFX i bulk RFX wymieniają dane między elementami członkowskimi danych pól obiektu zestawu rekordów i odpowiednimi polami bieżącego rekordu w źródle danych.

> [!NOTE]
> Jeśli pracujesz z klasami obiektów dostępu do danych (DAO), a nie klasami Open Database Connectivity (ODBC), zamiast tego użyj klasy [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) . Aby uzyskać więcej informacji, zobacz [Omówienie artykułu: Programowanie baz danych](../../data/data-access-programming-mfc-atl.md).

`CFieldExchange`Obiekt zawiera informacje kontekstu, które są konieczne do wymiany pól rekordów lub wymiany pól rekordów zbiorczych. `CFieldExchange`obiekty obsługują wiele operacji, w tym parametry powiązania i elementy członkowskie danych pól oraz ustawienia różnych flag dla pól bieżącego rekordu. Operacje RFX i bulk RFX są wykonywane na elementach członkowskich danych klasy zestawu rekordów typów zdefiniowanych przez wartość **`enum`** **FieldType** w `CFieldExchange` . Możliwe wartości **FieldType** to:

- `CFieldExchange::outputColumn`dla elementów członkowskich danych pola.

- `CFieldExchange::inputParam`lub `CFieldExchange::param` dla elementów członkowskich danych parametru wejściowego.

- `CFieldExchange::outputParam`dla elementów członkowskich danych parametrów wyjściowych.

- `CFieldExchange::inoutParam`dla elementów członkowskich danych parametru Input/Output.

Większość funkcji składowych klasy i składowych danych jest dostępnych do pisania własnych niestandardowych procedur RFX. Będziesz często korzystać z programu `SetFieldType` . Aby uzyskać więcej informacji, zobacz artykuł [wymienianie pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md) i [zestaw rekordów (ODBC)](../../data/odbc/recordset-odbc.md). Aby uzyskać informacje na temat pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułów: pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Aby uzyskać szczegółowe informacje o funkcjach globalnych RFX i bulk RFX, zobacz [Funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md) w sekcji makra MFC i Globals tego odwołania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CFieldExchange`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDB. h

## <a name="cfieldexchangeisfieldtype"></a><a name="isfieldtype"></a>CFieldExchange:: IsFieldType

Jeśli piszesz własną funkcję RFX, wywołaj `IsFieldType` na początku funkcji, aby określić, czy bieżącą operację można wykonać na konkretnym typie elementu członkowskiego danych pola lub parametru (a `CFieldExchange::outputColumn` , `CFieldExchange::inputParam` , `CFieldExchange::param` , `CFieldExchange::outputParam` lub `CFieldExchange::inoutParam` ).

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>Parametry

*pnField*<br/>
Numer sekwencyjny elementu członkowskiego danych pola lub parametru jest zwracany w tym parametrze. Ta liczba odnosi się do kolejności elementu członkowskiego danych w funkcji [CRecordset::D ofieldexchange](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [CRecordset::D obulkfieldexchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) .

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli bieżącą operację można wykonać na bieżącym typie pola lub parametru.

### <a name="remarks"></a>Uwagi

Postępuj zgodnie z modelem istniejących funkcji RFX.

## <a name="cfieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CFieldExchange:: SetFieldType

Potrzebujesz wywołania `SetFieldType` w zastąpieniu klasy zestawu rekordów [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) .

```cpp
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parametry

*nFieldType*<br/>
Wartość `enum FieldType` zadeklarowana w `CFieldExchange` , która może być jedną z następujących wartości:

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>Uwagi

W przypadku elementów członkowskich danych pola należy wywołać `SetFieldType` z parametrem `CFieldExchange::outputColumn` , po którym następuje wywołania funkcji RFX lub RFX BULK. Jeśli nie zaimplementowano pobierania wierszy zbiorczych, ClassWizard umieszcza to `SetFieldType` wywołanie w sekcji mapy pól w `DoFieldExchange` .

Jeśli Sparametryzuj swoją klasę zestawu rekordów, musisz wywołać ją `SetFieldType` ponownie, poza dowolną sekcją mapy pól, a następnie RFX wywołania dla wszystkich elementów członkowskich danych parametru. Każdy typ elementu członkowskiego danych musi mieć własne `SetFieldType` wywołanie. Poniższa tabela odróżnia różne wartości, które można przekazać do `SetFieldType` reprezentowania elementów członkowskich danych klasy:

|SetFieldType — wartość parametru|Typ elementu członkowskiego danych parametru|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|Parametr wejściowy. Wartość, która jest przenoszona do zapytania lub procedury składowanej zestawu rekordów.|
|`CFieldExchange::param` | Analogicznie jak `CFieldExchange::inputParam` .|
|`CFieldExchange::outputParam`|Parametr wyjściowy. Wartość zwracana procedury składowanej zestawu rekordów.|
|`CFieldExchange::inoutParam`|Parametr wejściowy/wyjściowy. Wartość, która jest przesyłana do i zwracana z procedury składowanej zestawu rekordów.|

Ogólnie rzecz biorąc każda grupa wywołań funkcji RFX skojarzonych z elementami członkowskimi danych pól lub składowymi danych parametrów musi być poprzedzona wywołaniem metody `SetFieldType` . Parametr *nFieldType* każdego `SetFieldType` wywołania identyfikuje typ elementów członkowskich danych reprezentowanych przez wywołania funkcji RFX, które są zgodne z `SetFieldType` wywołaniem.

Aby uzyskać więcej informacji na temat obsługi parametrów wyjściowych i wejściowych/wyjściowych, zobacz `CRecordset` funkcja członkowska [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Aby uzyskać więcej informacji na temat funkcji RFX i bulk RFX, zobacz temat [Funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md)tematu. Aby uzyskać informacje dotyczące pobierania wierszy zbiorczych, zobacz [zestaw rekordów artykułu: zbiorcze pobieranie rekordów (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

Ten przykład pokazuje kilka wywołań funkcji RFX z towarzyszącymi wywołaniami do `SetFieldType` . Należy zauważyć, że `SetFieldType` jest wywoływany przez `pFX` wskaźnik do `CFieldExchange` obiektu.

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
