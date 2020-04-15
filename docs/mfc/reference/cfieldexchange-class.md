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
ms.openlocfilehash: d4b99a4992075072253d4f9b3182a926673bdfd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373932"
---
# <a name="cfieldexchange-class"></a>Klasa CFieldExchange

Obsługuje procedury wymiany pól rekordów (RFX) i zbiorczej wymiany pól rekordów (Bulk RFX) używane przez klasy bazy danych.

## <a name="syntax"></a>Składnia

```
class CFieldExchange
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFieldExchange::IsFieldType](#isfieldtype)|Zwraca wartość niezerowa, jeśli bieżąca operacja jest odpowiednia dla typu aktualizowanego pola.|
|[CFieldExchange::SetFieldType](#setfieldtype)|Określa typ elementu członkowskiego danych zestawu rekordów — kolumny lub parametru — reprezentowanego `SetFieldType`przez wszystkie następujące wywołania funkcji RFX do następnego wywołania .|

## <a name="remarks"></a>Uwagi

`CFieldExchange`nie ma klasy podstawowej.

Tej klasy należy używać, jeśli piszesz procedury wymiany danych dla niestandardowych typów danych lub podczas implementowania pobierania wiersza zbiorczego; w przeciwnym razie nie będzie bezpośrednio używać tej klasy. RFX i Bulk RFX wymieniają dane między członkami pola obiektu zestaw rekordów i odpowiednie pola bieżącego rekordu w źródle danych.

> [!NOTE]
> Jeśli pracujesz z klasami obiektów dostępu do danych (DAO), a nie z klasami Open Database Connectivity (ODBC), należy użyć klasy [CDaoFieldExchange.](../../mfc/reference/cdaofieldexchange-class.md) Aby uzyskać więcej informacji, zobacz artykuł [Overview:Database Programming](../../data/data-access-programming-mfc-atl.md).

Obiekt `CFieldExchange` udostępnia informacje kontekstowe potrzebne do wymiany pól rekordów lub zbiorczej wymiany pól rekordów. `CFieldExchange`obiekty obsługują szereg operacji, w tym parametry wiązania i elementy członkowskie danych pól oraz ustawianie różnych flag na polach bieżącego rekordu. Operacje RFX i Bulk RFX są wykonywane na członkach danych klasy recordset typów zdefiniowanych przez **enum** **FieldType** w `CFieldExchange`programie . Możliwe wartości **FieldType** to:

- `CFieldExchange::outputColumn`dla elementów członkowskich danych terenowych.

- `CFieldExchange::inputParam`lub `CFieldExchange::param` dla elementów członkowskich danych parametrów wejściowych.

- `CFieldExchange::outputParam`dla elementów członkowskich danych parametrów wyjściowych.

- `CFieldExchange::inoutParam`dla elementów członkowskich parametrów wejścia/wyjścia.

Większość funkcji elementów członkowskich klasy i elementów członkowskich danych są dostarczane do pisania własnych procedur RFX niestandardowych. Będziesz często `SetFieldType` używać. Aby uzyskać więcej informacji, zobacz artykuły [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md) i [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Aby uzyskać informacje na temat pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Aby uzyskać szczegółowe informacje na temat globalnych funkcji RFX i Bulk RFX, zobacz [Rejestrowanie funkcji wymiany pól](../../mfc/reference/record-field-exchange-functions.md) w sekcji Makra I globalne MFC tego odwołania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CFieldExchange`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="cfieldexchangeisfieldtype"></a><a name="isfieldtype"></a>CFieldExchange::IsFieldType

Jeśli piszesz własną funkcję `IsFieldType` RFX, wywołanie na początku funkcji, aby ustalić, czy bieżąca operacja może `CFieldExchange::outputColumn` `CFieldExchange::inputParam`być `CFieldExchange::param` `CFieldExchange::outputParam`wykonana na określonym polu lub typie elementu członkowskiego danych parametru (a , , , , lub `CFieldExchange::inoutParam`).

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>Parametry

*pnField (polski)*<br/>
W tym parametrze zwracany jest kolejny numer elementu członkowskiego danych pola lub parametru. Liczba ta odpowiada kolejności elementu członkowskiego danych w [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [CRecordset::DoBulkFieldExchange.](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli bieżąca operacja może być wykonana na bieżącym polu lub typie parametru.

### <a name="remarks"></a>Uwagi

Postępuj zgodnie z modelem istniejących funkcji RFX.

## <a name="cfieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CFieldExchange::SetFieldType

Potrzebujesz wywołania `SetFieldType` w [dofieldexchange](../../mfc/reference/crecordset-class.md#dofieldexchange) klasy recordset lub [dobulkfieldexchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) zastąpić.

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parametry

*nPusty typ pola*<br/>
Wartość `enum FieldType`zadeklarowanej w `CFieldExchange`, która może być jedną z następujących wartości:

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>Uwagi

W przypadku elementów członkowskich `SetFieldType` danych pól `CFieldExchange::outputColumn`należy wywołać z parametrem , a następnie wywołaniem funkcji RFX lub bulk RFX. Jeśli pobieranie wierszy zbiorczych nie zostało zaimplementowane, program ClassWizard umieszcza to `SetFieldType` wywołanie w sekcji mapy pola w punkcie `DoFieldExchange`.

Jeśli parametryzujesz klasę zestaw rekordów, należy wywołać `SetFieldType` ponownie, poza sekcją mapy pola, a następnie rfx wywołania dla wszystkich elementów członkowskich danych parametru. Każdy typ elementu członkowskiego danych `SetFieldType` parametru musi mieć własne wywołanie. Poniższa tabela rozróżnia różne `SetFieldType` wartości, do których można przejść, aby reprezentować elementy członkowskie danych parametrów klasy:

|Wartość parametru SetFieldType|Typ elementu członkowskiego danych parametrów|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|Parametr wejściowy. Wartość przekazywana do kwerendy lub procedury składowanej pliku recordset.|
|`CFieldExchange::param` | tak `CFieldExchange::inputParam`samo jak .|
|`CFieldExchange::outputParam`|Parametr wyjściowy. Zwracana wartość procedury składowanej pliku recordset.|
|`CFieldExchange::inoutParam`|Parametr wejścia/wyjścia. Wartość, która jest przekazywana i zwracana z procedury składowanej pliku recordset.|

Ogólnie rzecz biorąc, każda grupa wywołań funkcji RFX skojarzonych z członkami danych `SetFieldType`pola lub członkami danych parametrów musi być poprzedzona wywołaniem . Parametr *nFieldType* każdego `SetFieldType` wywołania identyfikuje typ elementów członkowskich danych reprezentowanych przez wywołania funkcji RFX, które następują po wywołaniu. `SetFieldType`

Aby uzyskać więcej informacji na temat obsługi `CRecordset` parametrów wyjściowych i wejściowych/wyjściowych, zobacz funkcję elementu członkowskiego [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Aby uzyskać więcej informacji na temat funkcji RFX i bulk RFX, zobacz temat [Rejestrowanie funkcji wymiany pól](../../mfc/reference/record-field-exchange-functions.md). Aby uzyskać powiązane informacje dotyczące pobierania wierszy zbiorczych, zobacz artykuł [Rekord: Pobieranie rekordów zbiorczo (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

W tym przykładzie przedstawiono kilka wywołań `SetFieldType`funkcji RFX z towarzyszącymi połączeniami do . Należy `SetFieldType` zauważyć, że `pFX` jest `CFieldExchange` wywoływana przez wskaźnik do obiektu.

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
