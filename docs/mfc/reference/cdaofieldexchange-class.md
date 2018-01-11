---
title: Klasa CDaoFieldExchange | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
dev_langs: C++
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c4a62d3f9631d4e2807bf12e1eda3bd4b4f5112
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdaofieldexchange-class"></a>Klasa CDaoFieldExchange
Obsługuje procedury programu exchange (DFX) pól rekordów DAO używane przez klas baz danych DAO.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDaoFieldExchange  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|Zwraca wartość niezerową, jeśli bieżąca operacja jest odpowiednie dla typu pola aktualizowana.|  
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|Określa typ elementu członkowskiego danych rekordów — kolumna lub parametr — reprezentowany przez wszystkie kolejne wywołania funkcji DFX aż do następnego wywołania `SetFieldType`.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDaoFieldExchange::m_nOperation](#m_noperation)|DFX operacja wykonywana przez wywołanie bieżącego zestawu rekordów `DoFieldExchange` funkcję elementu członkowskiego.|  
|[CDaoFieldExchange::m_prs](#m_prs)|Wskaźnik do zestawu rekordów, na których DFX wykonywane są operacje.|  
  
## <a name="remarks"></a>Uwagi  
 `CDaoFieldExchange`nie ma klasy podstawowej.  
  
 Klasa używana podczas pisania procedury wymiany danych dla typów danych niestandardowych; w przeciwnym razie nie będzie bezpośrednio używany tej klasy. DFX wymianie danych między elementy członkowskie danych pola z Twojej [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiekt i odpowiednie pola z bieżącego rekordu w źródle danych. DFX zarządza programu exchange w obu kierunkach ze źródła danych i w źródle danych. Zobacz [53 Uwaga techniczna](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) informacje na temat pisania niestandardowe procedury DFX.  
  
> [!NOTE]
>  Klasy baz danych DAO różnią się od klasy baz danych MFC oparte na otwarte połączenie bazy danych (ODBC). Wszystkie nazwy klasy bazy danych DAO mają prefiks "CDao". Możesz nadal dostęp do źródła danych ODBC z klasy DAO. Ogólnie rzecz biorąc klas MFC DAO w oparciu nadają się bardziej niż klas MFC ODBC — na podstawie. Klasy oparte na DAO można uzyskać dostępu do danych, w tym za pomocą sterowników ODBC, za pomocą ich własnych aparatu bazy danych. Obsługują one również operacji języka definicji danych (DDL), takich jak dodawanie tabel za pomocą klasy zamiast wywołanie DAO samodzielnie.  
  
> [!NOTE]
>  Wymiana pól rekordów DAO (DFX) jest bardzo podobny do wymiana pól rekordów (RFX) w klasach bazy danych na podstawie ODBC MFC ( `CDatabase`, `CRecordset`). Jeśli znasz RFX będą dostępne DFX łatwy w użyciu.  
  
 A `CDaoFieldExchange` obiekt zapewnia informacje kontekstowe potrzebne do DAO wymiana pól rekordów została wykonana. `CDaoFieldExchange`obiekty obsługują szereg działań, włącznie z parametrów wiązania i elementy członkowskie danych pola i ustawienie flagi różnych pól bieżącego rekordu. DFX operacje są wykonywane na klasy rekordów elementy członkowskie danych typów zdefiniowanych przez `enum` **typu pola** w `CDaoFieldExchange`. Możliwe **typu pola** wartości to:  
  
- **CDaoFieldExchange::outputColumn** dla elementy członkowskie danych pola.  
  
- **CDaoFieldExchange::param** dla elementy członkowskie danych parametru.  
  
 [IsValidOperation](#isvalidoperation) funkcja członkowska jest dostępne w celu zapisywania własne niestandardowe procedury DFX. Użyjesz [SetFieldType](#setfieldtype) często w Twojej [CDaoRecordset::DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) funkcji. Aby uzyskać więcej informacji o funkcje globalne DFX, zobacz [funkcje wymiany pól rekordów](../../mfc/reference/record-field-exchange-functions.md). Informacje na temat pisania niestandardowe procedury DFX dla typów danych, zobacz [53 Uwaga techniczna](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CDaoFieldExchange`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
##  <a name="isvalidoperation"></a>CDaoFieldExchange::IsValidOperation  
 Jeśli piszesz funkcji DFX wywołanie `IsValidOperation` na początku funkcji do określenia, czy można wykonać bieżącej operacji na typ elementu członkowskiego danych określonego pola ( **CDaoFieldExchange::outputColumn** lub **CDaoFieldExchange::param**).  
  
```  
BOOL IsValidOperation();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli bieżąca operacja jest odpowiednia dla typu pola aktualizowana.  
  
### <a name="remarks"></a>Uwagi  
 Niektóre operacje wykonywane przez mechanizm DFX dotyczą tylko jeden z typów możliwych pola. Postępuj zgodnie z modelem istniejące funkcje DFX.  
  
 Aby uzyskać dodatkowe informacje o pisaniu niestandardowe procedury DFX, zobacz [53 Uwaga techniczna](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).  
  
##  <a name="m_noperation"></a>CDaoFieldExchange::m_nOperation  
 Identyfikuje operacji do wykonania na [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiekt powiązany z obiektem exchange pola.  
  
### <a name="remarks"></a>Uwagi  
 `CDaoFieldExchange` Obiektu dostarcza kontekst dla wielu różnych operacji DFX w zestawie rekordów.  
  
> [!NOTE]
>  **PSEUDONULL** opisanego w operacjach MarkForAddNew i SetFieldNull poniżej wartość jest wartością służy do oznaczania pola wartość Null. Mechanizm wymiany pól rekordów DAO (DFX) używa tej wartości, aby określić pola, które zostały jawnie oznaczone Null. **PSEUDONULL** nie jest wymagane dla [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) i [COleCurrency](../../mfc/reference/colecurrency-class.md) pól.  
  
 Możliwe wartości **m_nOperation** są:  
  
|Operacja|Opis|  
|---------------|-----------------|  
|**AddToParameterList**|Tworzy **parametry** klauzula instrukcji SQL.|  
|**AddToSelectList**|Tworzy **wybierz** klauzula instrukcji SQL.|  
|**BindField**|Wiąże pola w bazie danych z lokalizacji w pamięci w aplikacji.|  
|**BindParam**|Ustawia wartości parametrów dla kwerendy w zestawie rekordów.|  
|**Naprawy**|Ustawia stan wartości Null dla pola.|  
|**AllocCache**|Przydziela pamięć podręczna użytych do sprawdzenia pola "zakłóconych" w zestawie rekordów.|  
|**StoreField**|Zapisuje bieżący rekord w pamięci podręcznej.|  
|**LoadField**|Przywraca dane w pamięci podręcznej zmiennych w zestawie rekordów.|  
|**FreeCache**|Zwalnia pamięć podręczna użytych do sprawdzenia pola "zakłóconych" w zestawie rekordów.|  
|`SetFieldNull`|Ustawia stan tego pola wartość Null i wartość do **PSEUDONULL**.|  
|**MarkForAddNew**|Oznacza pola "zakłóconych", jeśli nie **PSEUDONULL**.|  
|**MarkForEdit**|Oznacza pola "zakłóconych", jeśli nie są zgodne pamięci podręcznej.|  
|**SetDirtyField**|Ustawia pole wartości oznaczone jako "zakłóconych".|  
|**DumpField**|Zrzuty zawartość pola (tylko debugowanie).|  
|**MaxDFXOperation**|Używany do sprawdzania wejściowego.|  
  
##  <a name="m_prs"></a>CDaoFieldExchange::m_prs  
 Zawiera wskaźnik do [cdaorecordset —](../../mfc/reference/cdaorecordset-class.md) obiekt skojarzony z `CDaoFieldExchange` obiektu.  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="setfieldtype"></a>CDaoFieldExchange::SetFieldType  
 Wywołanie `SetFieldType` w Twojej `CDaoRecordset` klasy `DoFieldExchange` zastąpienia.  
  
```  
void SetFieldType(UINT nFieldType);
```  
  
### <a name="parameters"></a>Parametry  
 `nFieldType`  
 Wartość **wyliczenia typu pola**, zadeklarowanych w `CDaoFieldExchange`, który może być jedną z następujących czynności:  
  
- **CDaoFieldExchange::outputColumn**  
  
- **CDaoFieldExchange::param**  
  
### <a name="remarks"></a>Uwagi  
 Zwykle ClassWizard zapisuje to wywołanie za Ciebie. Jeśli Napisz własną funkcję, a za pomocą kreatora można zapisać Twoje `DoFieldExchange` funkcji, należy dodać wywołania funkcji poza mapowanie pola. Jeśli nie używasz kreatora, nie zostanie mapy pól. Wywołanie poprzedza wywołania funkcji DFX, jeden dla każdego elementu członkowskiego danych pola klasy i określa typ pola jako **CDaoFieldExchange::outputColumn**.  
  
 Jeśli parametryzacja zestawu rekordów klasy, Dodaj wywołania DFX wszystkie elementy członkowskie danych parametru (poza mapowanie pola) i poprzedzać tych wywołań w wyniku wywołania `SetFieldType`. Przekaż wartość **CDaoFieldExchange::param**. (Zamiast tego można użyć [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) i ustawić jej wartości parametrów.)  
  
 Ogólnie rzecz biorąc, każdej grupy DFX wywołania funkcji związanych z elementy członkowskie danych pola lub elementy członkowskie danych parametru musi być poprzedzony przez wywołanie do `SetFieldType`. `nFieldType` Parametru każdego `SetFieldType` wywołania Określa typ elementów członkowskich danych reprezentowanego przez DFX wywołania funkcji, które należy wykonać `SetFieldType` wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)
