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
ms.openlocfilehash: e66b3ed16d4f21d46567c37bfaf7929d32f63b8e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294983"
---
# <a name="cfieldexchange-class"></a>Klasa CFieldExchange

Obsługuje procedury wymiany (zbiorcze RFX) zbiorczej pól rekordów z używanych przez klasy bazy danych i wymiana pól rekordów (RFX).

## <a name="syntax"></a>Składnia

```
class CFieldExchange
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFieldExchange::IsFieldType](#isfieldtype)|Zwraca wartość różną od zera, jeśli bieżąca operacja jest odpowiednie dla typu pola aktualizowana.|
|[CFieldExchange::SetFieldType](#setfieldtype)|Określa typ element członkowski danych rekordów — kolumna lub parametr — reprezentowany przez wszystkie następujące wywołania funkcji RFX aż do następnego wywołania metody `SetFieldType`.|

## <a name="remarks"></a>Uwagi

`CFieldExchange` nie ma klasy bazowej.

Klasa jest używana podczas pisania procedury wymiany danych dla niestandardowych typów danych lub gdy w przypadku wdrażania zbiorcze pobieranie z wiersza; w przeciwnym razie nie bezpośrednio użyjesz tej klasy. RFX zbiorcze RFX wymiany danych oraz między elementy członkowskie danych pola obiektu zestawu rekordów i odpowiednich pól bieżącego rekordu w źródle danych.

> [!NOTE]
>  Jeśli pracujesz z klas obiektów dostępu do danych (DAO), a nie klasy Open Database Connectivity (ODBC), należy użyć klasy [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) zamiast tego. Aby uzyskać więcej informacji, zobacz artykuł [baza danych — omówienie programowania](../../data/data-access-programming-mfc-atl.md).

A `CFieldExchange` obiekt zapewnia informacje kontekstowe potrzebne wymiana pól rekordów lub zbiorcza wymiana pól rekordów, aby móc umieścić. `CFieldExchange` obiekty obsługują szereg operacji, takich jak parametry powiązania i elementy członkowskie danych pola oraz ustawienie flagi różnych pól bieżącego rekordu. RFX i zbiorcze RFX operacje są wykonywane na składowych danych klas zestawu rekordów typy zdefiniowane przez **wyliczenia** **typu pola** w `CFieldExchange`. Możliwe **typu pola** wartości to:

- `CFieldExchange::outputColumn` Aby uzyskać elementy członkowskie danych pola.

- `CFieldExchange::inputParam` lub `CFieldExchange::param` składowych danych parametru wejściowego.

- `CFieldExchange::outputParam` Aby uzyskać dane wyjściowe elementy członkowskie danych parametru.

- `CFieldExchange::inoutParam` Parametr input/output składowych danych.

Większość elementów członkowskich funkcje i dane Członkowskie tej klasy są dostarczane do pisania własnych niestandardowych procedury RFX. Użyjesz `SetFieldType` często. Aby uzyskać więcej informacji, zobacz artykuły [wymiany pól rekordu (RFX)](../../data/odbc/record-field-exchange-rfx.md) i [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md). Aby dowiedzieć się, jak zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: Pobieranie rekordów (ODBC) zbiorcze](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Aby uzyskać szczegółowe informacje dotyczące funkcji globalnych RFX i zbiorcze RFX, zobacz [funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md) makr MFC i funkcje globalne sekcji tego odwołania.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CFieldExchange`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

##  <a name="isfieldtype"></a>  CFieldExchange::IsFieldType

Jeśli piszesz funkcji RFX, wywołaj `IsFieldType` na początku funkcję, aby określić, czy bieżący operację można wykonać określonego pola lub parametru elementu członkowskiego typu danych ( `CFieldExchange::outputColumn`, `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`, lub `CFieldExchange::inoutParam`).

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>Parametry

*pnField*<br/>
Numer porządkowy pola lub parametr składowej danych, które jest zwracany w tym parametrze. Ta liczba odpowiada kolejności składowej danych w [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [CRecordset::DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) funkcji.

### <a name="return-value"></a>Wartość zwracana

Różna od zera, jeśli dla bieżącego pola lub parametru typu można wykonać bieżącej operacji.

### <a name="remarks"></a>Uwagi

Postępuj zgodnie z modelem istniejące funkcje RFX.

##  <a name="setfieldtype"></a>  CFieldExchange::SetFieldType

Konieczne jest wywołanie `SetFieldType` w klasie rekordów [dofieldexchange —](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [dobulkfieldexchange —](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) zastąpienia.

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parametry

*nFieldType*<br/>
Wartość `enum FieldType`, zadeklarowanych w `CFieldExchange`, który może być jedną z następujących czynności:

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>Uwagi

Elementy członkowskie danych pola, należy wywołać `SetFieldType` z parametrem `CFieldExchange::outputColumn`, a następnie wywołania funkcji RFX lub zbiorcze RFX. Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza, a następnie umieszcza ClassWizard, to `SetFieldType` wywołać dla Ciebie w sekcji map pola `DoFieldExchange`.

Jeśli możesz zdefiniować parametry klasy zestawu rekordów, należy wywołać `SetFieldType` ponownie poza dowolną sekcję mapy pola następuje RFX wywołań dla wszystkich członków danych parametru. Każdy typ element członkowski danych parametr musi mieć swój własny `SetFieldType` wywołania. Poniższa tabela różnic między usługą różne wartości, którą można przekazać do `SetFieldType` do reprezentowania elementy członkowskie danych parametru klasy:

|Wartość parametru SetFieldType|Typ parametru element członkowski danych|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|Parametr wejściowy. Wartość, która została przekazana do zapytań lub procedurze składowanej w zestawie rekordów.|
|`CFieldExchange::param` | Taki sam jak `CFieldExchange::inputParam`.|
|`CFieldExchange::outputParam`|Parametr wyjściowy. Zwracana wartość wynosząca procedury składowanej w zestawie rekordów.|
|`CFieldExchange::inoutParam`|Parametr input/output. Wartość, która jest przekazywana do i zwrócone przez procedurę składowaną w zestawie rekordów.|

Ogólnie rzecz biorąc, poszczególne grupy skojarzone z elementy członkowskie danych pola lub elementy członkowskie danych parametru wywołania funkcji RFX musi być poprzedzona wywołanie `SetFieldType`. *NFieldType* parametru każdego `SetFieldType` wywołanie określa typ elementów członkowskich danych reprezentowanego przez wywołania funkcji RFX, które należy wykonać `SetFieldType` wywołania.

Aby uzyskać więcej informacji na temat obsługi danych wyjściowych i parametrów wejściowych/wyjściowych zobacz `CRecordset` funkcja elementu członkowskiego [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Aby uzyskać więcej informacji na temat funkcji RFX i zbiorcze RFX, zobacz temat [funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md). Aby uzyskać powiązane informacje na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: Pobieranie rekordów (ODBC) zbiorcze](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Przykład

W tym przykładzie pokazano kilka wywołań do funkcji RFX z towarzyszącym wywołania `SetFieldType`. Należy pamiętać, że `SetFieldType` jest wywoływany za pośrednictwem `pFX` wskaźnik do `CFieldExchange` obiektu.

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CRecordset](../../mfc/reference/crecordset-class.md)
