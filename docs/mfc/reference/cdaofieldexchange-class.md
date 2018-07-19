---
title: Klasa CDaoFieldExchange | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
dev_langs:
- C++
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f5f4de25c0ed4643f93626f92a83942c70dfce5
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337843"
---
# <a name="cdaofieldexchange-class"></a>Klasa CDaoFieldExchange
Obsługuje procedury wymiany (DXF) pola rekordów DAO używanych przez klasy bazy danych DAO.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDaoFieldExchange  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|Zwraca wartość różną od zera, jeśli bieżąca operacja jest odpowiednie dla typu pola aktualizowana.|  
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|Określa typ element członkowski danych rekordów — kolumna lub parametr — reprezentowany przez wszystkie kolejne wywołania funkcji DFX aż do następnego wywołania metody `SetFieldType`.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoFieldExchange::m_nOperation](#m_noperation)|Operacja DFX wykonywanego przez bieżącego wywołania do zestawu rekordów `DoFieldExchange` funkcja elementu członkowskiego.|  
|[CDaoFieldExchange::m_prs](#m_prs)|Wskaźnik do zestawu rekordów, na które DFX operacje są wykonywane.|  
  
## <a name="remarks"></a>Uwagi  
 `CDaoFieldExchange` nie ma klasy bazowej.  
  
 Klasa jest używana podczas pisania procedury wymiany danych dla niestandardowych typów danych; w przeciwnym razie nie bezpośrednio użyjesz tej klasy. DFX wymienia dane między elementy członkowskie danych pola z Twojej [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiektu i odpowiednich pól bieżącego rekordu w źródle danych. DFX zarządza programu exchange w obu kierunkach, ze źródła danych i źródłem danych. Zobacz [techniczne 53 Uwaga](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) informacje na temat pisania niestandardowe procedury DFX.  
  
> [!NOTE]
>  Klasy bazy danych DAO różnią się od klas baz danych MFC, które są oparte na Open Database Connectivity (ODBC). Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Możesz nadal dostęp do źródła danych ODBC przy użyciu klas DAO. Ogólnie rzecz biorąc klas MFC DAO w oparciu nadają się bardziej niż klas MFC, w oparciu o ODBC. Klasy oparte na DAO można uzyskać dostęp do danych, w tym za pomocą sterowników ODBC, za pomocą ich własnych aparatu bazy danych. Obsługują one również operacji języka definicji danych (DDL), takich jak dodawanie tablic za pomocą klasy nie trzeba samodzielnie wywoływanie obiektów DAO.  
  
> [!NOTE]
>  Wymiana pól rekordów DAO (DXF) jest bardzo podobny do wymiana pól rekordów (RFX) w klasach MFC ODBC, na podstawie bazy danych ( `CDatabase`, `CRecordset`). Jeśli rozumiesz RFX znajdziesz go DFX łatwy w użyciu.  
  
 A `CDaoFieldExchange` obiekt zapewnia informacje kontekstowe potrzebne do DAO wymiana pól rekordów została wykonana. `CDaoFieldExchange` obiekty obsługują szereg operacji, takich jak parametry powiązania i elementy członkowskie danych pola oraz ustawienie flagi różnych pól bieżącego rekordu. DFX operacje są wykonywane na składowych danych klas zestawu rekordów typy zdefiniowane przez **wyliczenia** **typu pola** w `CDaoFieldExchange`. Możliwe **typu pola** wartości to:  
  
- `CDaoFieldExchange::outputColumn` Aby uzyskać elementy członkowskie danych pola.  
  
- `CDaoFieldExchange::param` Aby uzyskać elementy członkowskie danych parametru.  
  
 [IsValidOperation](#isvalidoperation) do pisania własne niestandardowe procedury DFX znajduje się funkcja elementu członkowskiego. Użyjesz [SetFieldType](#setfieldtype) często w swojej [CDaoRecordset::DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) funkcji. Aby uzyskać szczegółowe informacje dotyczące funkcji globalnych DFX, zobacz [funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md). Aby dowiedzieć się, jak pisanie niestandardowe procedury DFX dla typów danych, zobacz [techniczne 53 Uwaga](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CDaoFieldExchange`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
##  <a name="isvalidoperation"></a>  CDaoFieldExchange::IsValidOperation  
 Jeśli piszesz funkcji DFX, wywołaj `IsValidOperation` na początku funkcję, aby określić, czy bieżąca operacja można przeprowadzić na typ element członkowski danych określonego pola ( `CDaoFieldExchange::outputColumn` lub `CDaoFieldExchange::param`).  
  
```  
BOOL IsValidOperation();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli bieżąca operacja jest odpowiednia dla typu pola aktualizowana.  
  
### <a name="remarks"></a>Uwagi  
 Niektóre operacje wykonywane przez mechanizm DFX dotyczą tylko jednego z typów możliwych pól. Postępuj zgodnie z modelem istniejące funkcje DFX.  
  
 Aby uzyskać dodatkowe informacje na temat pisania niestandardowe procedury DFX, zobacz [techniczne 53 Uwaga](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
##  <a name="m_noperation"></a>  CDaoFieldExchange::m_nOperation  
 Określa operację do wykonania na [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiekt skojarzony z obiektem wymiany pól.  
  
### <a name="remarks"></a>Uwagi  
 `CDaoFieldExchange` Obiektu dostarcza kontekst dla szeregu różnych operacji DFX na zestaw rekordów.  
  
> [!NOTE]
>  Wartość PSEUDONULL opisane w sekcji poniżej operacje MarkForAddNew i SetFieldNull jest wartością używany do oznaczania pól o wartości Null. Mechanizm wymiany pól rekordów DAO (DXF) używa tej wartości, aby określić pola, które zostały jawnie oznaczone jako Null. Nie jest wymagane dla PSEUDONULL [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) i [COleCurrency](../../mfc/reference/colecurrency-class.md) pola.  
  
 Możliwe wartości `m_nOperation` są:  
  
|Operacja|Opis|  
|---------------|-----------------|  
|`AddToParameterList`|Kompilacje **parametry** klauzula instrukcji SQL.|  
|`AddToSelectList`|Kompilacje **wybierz** klauzula instrukcji SQL.|  
|`BindField`|Wiąże pola w bazie danych z lokalizacji w pamięci w aplikacji.|  
|`BindParam`|Ustawia wartości parametrów dla kwerendy w zestawie rekordów.|  
|`Fixup`|Ustawia stan o wartości Null dla pola.|  
|`AllocCache`|Przydziela pamięć podręczna użytych do sprawdzenia, czy pola "zakłóconych" w zestawie rekordów.|  
|`StoreField`|Zapisuje bieżący rekord w pamięci podręcznej.|  
|`LoadField`|Przywraca dane w pamięci podręcznej zmiennych w zestawie rekordów.|  
|`FreeCache`|Zwalnia pamięć podręczna użytych do sprawdzenia, czy pola "zakłóconych" w zestawie rekordów.|  
|`SetFieldNull`|Ustawia stan tego pola wartość Null i wartości do PSEUDONULL.|  
|`MarkForAddNew`|Znaki pól "zakłóconych" Jeśli nie PSEUDONULL.|  
|`MarkForEdit`|Pola oznacza "zanieczyszczony", jeśli nie są zgodne pamięci podręcznej.|  
|`SetDirtyField`|Ustawia pole wartości oznaczone jako "zakłóconych".|  
|`DumpField`|Zrzuty zawartość pola (tylko debugowanie).|  
|`MaxDFXOperation`|Używany do sprawdzania danych wejściowych.|  
  
##  <a name="m_prs"></a>  CDaoFieldExchange::m_prs  
 Zawiera wskaźnik do [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) obiekt skojarzony z `CDaoFieldExchange` obiektu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setfieldtype"></a>  CDaoFieldExchange::SetFieldType  
 Wywołaj `SetFieldType` w swojej `CDaoRecordset` klasy `DoFieldExchange` zastąpienia.  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>Parametry  
 *nFieldType*  
 Wartość **wyliczenia typu pola**, zadeklarowanych w `CDaoFieldExchange`, który może być jedną z następujących czynności:  
  
- `CDaoFieldExchange::outputColumn`  
  
- `CDaoFieldExchange::param`  
  
### <a name="remarks"></a>Uwagi  
 Normalnie ClassWizard zapisuje to wywołanie dla Ciebie. Możesz napisać własną funkcję i za pomocą kreatora można zapisać swoje `DoFieldExchange` działać i dodawać wywołania do funkcji poza mapowanie pola. Jeśli nie używasz kreatora, nie nastąpi mapowanie pola. Wywołanie poprzedza wywołania funkcje DFX, jeden dla każdego elementu członkowskiego danych pola klasy i identyfikuje typ pola jako `CDaoFieldExchange::outputColumn`.  
  
 Jeśli możesz zdefiniować parametry klasy zestawu rekordów, Dodaj wywołania DFX dla wszystkie elementy członkowskie danych parametru (poza mapowanie pola) i poprzedzają te wywołania z wywołaniem `SetFieldType`. Przekaż wartość `CDaoFieldExchange::param`. (Zamiast tego można użyć [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) i ustaw jego wartości parametru.)  
  
 Ogólnie rzecz biorąc, poszczególne grupy DFX wywołania funkcji związanych z elementy członkowskie danych pola lub elementy członkowskie danych parametru musi być poprzedzona wywołanie `SetFieldType`. *NFieldType* parametru każdego `SetFieldType` wywołanie określa typ elementów członkowskich danych reprezentowanego przez wywołania funkcji DFX, które należy wykonać `SetFieldType` wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)
