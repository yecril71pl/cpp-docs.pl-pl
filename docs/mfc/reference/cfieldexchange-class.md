---
title: Klasa CFieldExchange | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
dev_langs:
- C++
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bad68253525fd728b67f2e256c48a3edbf48d720
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cfieldexchange-class"></a>Klasa CFieldExchange
Obsługuje wymiana pól rekordów (RFX) i procedury wymiany (zbiorczego RFX) pól rekordów zbiorczego używane przez klasy baz danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CFieldExchange  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFieldExchange::IsFieldType](#isfieldtype)|Zwraca wartość niezerową, jeśli bieżąca operacja jest odpowiednie dla typu pola aktualizowana.|  
|[CFieldExchange::SetFieldType](#setfieldtype)|Określa typ elementu członkowskiego danych rekordów — kolumna lub parametr — reprezentowany przez wszystkie wywołania następujące funkcje RFX aż do następnego wywołania `SetFieldType`.|  
  
## <a name="remarks"></a>Uwagi  
 `CFieldExchange` nie ma klasy podstawowej.  
  
 Klasa używana podczas pisania procedury wymiany danych w niestandardowe typy danych lub gdy w przypadku implementowania zbiorcze pobieranie z wiersza; w przeciwnym razie nie będzie bezpośrednio używany tej klasy. RFX i RFX zbiorczego wymianie danych między elementy członkowskie danych pola obiektu zestawu rekordów i odpowiednie pola z bieżącego rekordu w źródle danych.  
  
> [!NOTE]
>  Jeśli pracujesz z klas obiektów DAO (Data Access), a nie klasy otwarte połączenie bazy danych (ODBC), należy użyć klasy [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) zamiast tego. Aby uzyskać więcej informacji, zobacz artykuł [programowania omówienie: baza danych](../../data/data-access-programming-mfc-atl.md).  
  
 A `CFieldExchange` obiekt zapewnia informacje kontekstowe potrzebne wymiana pól rekordów lub zbiorcza wymiana pól rekordów podjęcie Umieść. `CFieldExchange` obiekty obsługują szereg działań, włącznie z parametrów wiązania i elementy członkowskie danych pola i ustawienie flagi różnych pól bieżącego rekordu. RFX i RFX zbiorcze operacje są wykonywane na klasy rekordów elementy członkowskie danych typów zdefiniowanych przez `enum` **typu pola** w `CFieldExchange`. Możliwe **typu pola** wartości to:  
  
- **CFieldExchange::outputColumn** dla elementy członkowskie danych pola.  
  
- **CFieldExchange::inputParam** lub **CFieldExchange::param** elementów członkowskich danych parametru wejściowego.  
  
- **CFieldExchange::outputParam** dla elementy członkowskie danych parametru w danych wyjściowych.  
  
- **CFieldExchange::inoutParam** dla elementy członkowskie danych parametru wejścia/wyjścia.  
  
 Większość elementów członkowskich danych i funkcje elementu członkowskiego klasy są dostarczane do pisania własne niestandardowe procedury RFX. Użyjesz `SetFieldType` często. Aby uzyskać więcej informacji, zobacz artykuły [wymiany pól rekordów (RFX)](../../data/odbc/record-field-exchange-rfx.md) i [zestawu rekordów (ODBC)](../../data/odbc/recordset-odbc.md). Aby uzyskać informacje na temat zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Aby uzyskać więcej informacji o globalne funkcje RFX i RFX zbiorczego, zobacz [funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md) w sekcji makr MFC i funkcje globalne tego odwołania.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CFieldExchange`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  
  
##  <a name="isfieldtype"></a>  CFieldExchange::IsFieldType  
 Jeśli piszesz funkcji RFX wywołanie `IsFieldType` na początku funkcji do określenia, czy można wykonać bieżącej operacji na określonego typu elementu członkowskiego danych pola lub parametr ( **CFieldExchange::outputColumn**, **CFieldExchange::inputParam**, **CFieldExchange::param**, **CFieldExchange::outputParam**, lub **CFieldExchange::inoutParam** ).  
  
```  
BOOL IsFieldType(UINT* pnField);
```  
  
### <a name="parameters"></a>Parametry  
 *pnField*  
 Numer porządkowy pola lub parametr elementu członkowskiego danych jest zwracana w tym parametrze. Liczba odpowiada kolejności element członkowski danych w [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [CRecordset::DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) funkcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli bieżącą operację można wykonać na bieżący typ pola lub parametr.  
  
### <a name="remarks"></a>Uwagi  
 Postępuj zgodnie z modelem istniejące funkcje RFX.  
  
##  <a name="setfieldtype"></a>  CFieldExchange::SetFieldType  
 Należy wywołanie `SetFieldType` w klasie rekordów [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) lub [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) zastąpienia.  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>Parametry  
 `nFieldType`  
 Wartość **wyliczenia typu pola**, zadeklarowanych w `CFieldExchange`, który może być jedną z następujących czynności:  
  
- **CFieldExchange::outputColumn**  
  
- **CFieldExchange::inputParam**  
  
- **CFieldExchange::param**  
  
- **CFieldExchange::outputParam**  
  
- **CFieldExchange::inoutParam**  
  
### <a name="remarks"></a>Uwagi  
 Elementy członkowskie danych pola, należy wywołać `SetFieldType` z parametrem **CFieldExchange::outputColumn**, a następnie wywołania funkcji RFX lub RFX zbiorczego. Jeśli nie zaimplementowano zbiorcze pobieranie z wiersza, a następnie powoduje ClassWizard, to `SetFieldType` wywołania dla Ciebie w sekcji map pola `DoFieldExchange`.  
  
 Jeśli parametryzacja zestawu rekordów klasy, należy wywołać `SetFieldType` ponownie, poza dowolnej sekcji mapy pola następuje wywołania RFX dla wszystkich członków danych parametru. Każdy typ elementu członkowskiego danych parametru musi mieć własny `SetFieldType` wywołania. Poniższa tabela odróżnia różne wartości, które można przekazać do `SetFieldType` do reprezentowania elementy członkowskie danych parametru klasy:  
  
|Wartość parametru SetFieldType|Typ elementu członkowskiego danych parametru|  
|----------------------------------|-----------------------------------|  
|**CFieldExchange::inputParam**|Parametr wejściowy. Wartość, która została przekazana do zapytań lub procedurze składowanej w zestawie rekordów.|  
|**CFieldExchange::param**|Taki sam jak **CFieldExchange::inputParam**.|  
|**CFieldExchange::outputParam**|Parametr wyjściowy. Procedury składowanej zwracana wartość w zestawie rekordów.|  
|**CFieldExchange::inoutParam**|Parametr wejścia/wyjścia. Wartość, która jest przekazany i zwrócony z procedury składowanej w zestawie rekordów.|  
  
 Ogólnie rzecz biorąc, każdej grupy wywołania funkcji RFX skojarzonych z elementy członkowskie danych pola lub elementy członkowskie danych parametru musi być poprzedzony przez wywołanie do `SetFieldType`. `nFieldType` Parametru każdego `SetFieldType` wywołania Określa typ elementów członkowskich danych reprezentowanego przez wywołania funkcji RFX, które należy wykonać `SetFieldType` wywołania.  
  
 Aby uzyskać więcej informacji na temat obsługi parametry wejścia/wyjścia i danych wyjściowych, zobacz `CRecordset` funkcji członkowskiej [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Aby uzyskać więcej informacji o funkcji RFX i RFX zbiorczego, zobacz temat [funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md). Powiązane informacje zbiorcze pobieranie z wiersza, zobacz artykuł [zestaw rekordów: pobieranie rekordów zbiorczego (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
### <a name="example"></a>Przykład  
 W tym przykładzie pokazano kilka wywołania funkcji RFX z towarzyszącym wywołania `SetFieldType`. Należy pamiętać, że `SetFieldType` jest wywoływana przez `pFX` wskaźnik do `CFieldExchange` obiektu.  
  
 [!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CRecordset](../../mfc/reference/crecordset-class.md)
