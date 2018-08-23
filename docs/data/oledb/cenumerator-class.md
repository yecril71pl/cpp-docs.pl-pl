---
title: Klasa CEnumerator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CEnumerator
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
dev_langs:
- C++
helpviewer_keywords:
- CEnumerator class
- Find method
- GetMoniker method
- Open method
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 604b28147c6881c7b2d62c388c5402f12bb71c78
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464748"
---
# <a name="cenumerator-class"></a>Klasa CEnumerator
Używa obiekt modułu wyliczającego OLE DB, który uwidacznia [ISourcesRowset](/previous-versions/windows/desktop/ms715969\(v=vs.85\)) interfejsu, aby zwrócić zestaw wierszy opisujące wszystkich źródeł danych i modułów wyliczających.  
  
## <a name="syntax"></a>Składnia

```cpp
class CEnumerator :   
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>  
```  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Znajdź](#find)|Wyszukuje dostępnych dostawców (źródła danych), wyszukiwania dla jednej z określoną nazwą.|  
|[GetMoniker](#getmoniker)|Pobiera `IMoniker` interfejsu dla bieżącego rekordu.|  
|[Otwórz](#open)|Zostanie otwarty modułu wyliczającego.|  
  
## <a name="remarks"></a>Uwagi  
 Możesz pobrać `ISourcesRowset` danych pośrednio od tej klasy.  

## <a name="find"></a> CEnumerator::Find
Wyszukuje określoną nazwą wśród dostępnych dostawców.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
bool Find(TCHAR* szSearchName) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *szSearchName*  
 [in] Nazwa do wyszukania.  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli nazwa została znaleziona. W przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Ta nazwa jest mapowana do `SOURCES_NAME` członkiem [ISourcesRowset](/previous-versions/windows/desktop/ms715969\(v=vs.85\)) interfejsu.  
  
## <a name="getmoniker"></a> CEnumerator::GetMoniker
Analizuje nazwę wyświetlaną, aby wyodrębnić składnika ciąg, który można przekonwertować na krótka.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();  

HRESULT GetMoniker(LPMONIKER* ppMoniker,   
   LPCTSTR lpszDisplayName) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *ppMoniker*  
 [out] Moniker pochodzącą z nazwy wyświetlanej analizy ([CEnumeratorAccessor::m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) bieżącego wiersza.  
  
 *lpszDisplayName*  
 [in] Nazwa wyświetlana, można przeanalizować.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  

## <a name="open"></a> CEnumerator::Open
Wiąże monikera programu dla typu wyliczeniowego, jeśli jeden jest określony, a następnie pobiera zestaw wierszy dla modułu wyliczającego, wywołując [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200\(v=vs.85\)).  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT Open(LPMONIKER pMoniker) throw();  

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();  

HRESULT Open(const CEnumerator& enumerator) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *pMoniker*  
 [in] Wskaźnik do moniker moduł wyliczający.  
  
 *pClsid*  
 [in] Wskaźnik do `CLSID` modułu wyliczającego.  
  
 *enumerator*  
 [in] Odwołanie do modułu wyliczającego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  
  
## <a name="see-also"></a>Zobacz też  
 [DBViewer](../../visual-cpp-samples.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)