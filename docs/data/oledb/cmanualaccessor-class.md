---
title: Cmanualaccessor — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CManualAccessor class
- AddBindEntry method
- AddParameterEntry method
- CreateAccessor method
- CreateParameterAccessor method
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f94e1100398b3f338fdc34839aee9a1e8f67871c
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338379"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor — Klasa
Reprezentuje typ metody dostępu przeznaczony dla zaawansowanych użytkowników.  
  
## <a name="syntax"></a>Składnia

```cpp
class CManualAccessor : public CAccessorBase  
```  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddBindEntry](#addbindentry)|Dodaje wpis powiązanie kolumn danych wyjściowych.|  
|[AddParameterEntry](#addparameterentry)|Dodaje wpis parametru do metody dostępu parametru.|  
|[CreateAccessor](#createaccessor)|Przydziela pamięć dla kolumny struktury powiązania i inicjuje elementy członkowskie danych kolumny.|  
|[Createparameteraccessor —](#createparameteraccessor)|Przydziela pamięć dla parametru powiązania struktury i inicjuje elementy członkowskie danych parametru.|  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą `CManualAccessor`, można określić parametr i powiązanie kolumny danych wyjściowych przez funkcję wywołania funkcji środowiska uruchomieniowego.  

## <a name="addbindentry"></a> CManualAccessor::AddBindEntry
Dodaje wpis powiązanie kolumn danych wyjściowych.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
void AddBindEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) w *OLE DB Podręcznik programisty*.  
  
 *nOrdinal*  
 [in] Numer kolumny.  
  
 *wType*  
 [in] Typ danych.  
  
 *nColumnSize*  
 [in] Kolumna rozmiar w bajtach.  
  
 *pData*  
 [in] Wskaźnik do danych kolumny, przechowywane w buforze.  
  
 *pLength*  
 [in] Wskaźnik do długość pola, jeśli jest to wymagane.  
  
 *pStatus*  
 [in] Wskaźnik do zmiennej może być powiązane z stan kolumny, jeśli jest to wymagane.  
  
### <a name="remarks"></a>Uwagi  
 Aby użyć tej funkcji, należy najpierw wywołać [createaccessor —](../../data/oledb/cmanualaccessor-createaccessor.md). Nie można dodać więcej wpisów niż liczba kolumn określona w `CreateAccessor`. 
  
## <a name="addparameterentry"></a> CManualAccessor::AddParameterEntry
Dodaje wpis parametr do parametru struktury wpisu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
void AddParameterEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL,  
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobacz [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) w *OLE DB Podręcznik programisty*.  
  
 *nOrdinal*  
 [in] Liczba parametrów.  
  
 *wType*  
 [in] Typ danych.  
  
 *nColumnSize*  
 [in] Kolumna rozmiar w bajtach.  
  
 *pData*  
 [in] Wskaźnik do danych kolumny, przechowywane w buforze.  
  
 *pLength*  
 [in] Wskaźnik do długość pola, jeśli jest to wymagane.  
  
 *pStatus*  
 [in] Wskaźnik do zmiennej może być powiązane z stan kolumny, jeśli jest to wymagane.  
  
 *eParamIO*  
 [in] Określa, czy parametr, z którym jest skojarzona wiązanie parametru wejściowego, wejścia/wyjścia lub dane wyjściowe.  
  
### <a name="remarks"></a>Uwagi  
 Aby użyć tej funkcji, należy najpierw wywołać [createparameteraccessor —](../../data/oledb/cmanualaccessor-createparameteraccessor.md). 

## <a name="createaccessor"></a> CManualAccessor::CreateAccessor
Przydziela pamięć dla kolumny struktury powiązania i inicjuje elementy członkowskie danych kolumny.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateAccessor(int nBindEntries,   
  void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nBindEntries*  
 [in] Liczba kolumn. Liczba ta powinna odpowiadać liczbie wywołań [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) funkcji.  
  
 *pBuffer*  
 [in] Wskaźnik do buforu, gdzie są przechowywane kolumn wyjściowych.  
  
 *nBufferSize*  
 [in] Rozmiar buforu w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jedna z wartości HRESULT standardowych.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę funkcję, zanim wywołasz `CManualAccessor::AddBindEntry` funkcji.  

## <a name="createparameteraccessor"></a> CManualAccessor::CreateParameterAccessor
Przydziela pamięć dla parametru powiązania struktury i inicjuje elementy członkowskie danych parametru.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CreateParameterAccessor(int nBindEntries,   
   void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nBindEntries*  
 [in] Liczba kolumn.  
  
 *pBuffer*  
 [in] Wskaźnik do buforu, w którym kolumny wejściowe są przechowywane.  
  
 *nBufferSize*  
 [in] Rozmiar buforu w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jedna z wartości HRESULT standardowych.  
  
### <a name="remarks"></a>Uwagi  
 Musisz wywołać tę funkcję, przed wywołaniem [addparameterentry —](../../data/oledb/cmanualaccessor-addparameterentry.md).

## <a name="see-also"></a>Zobacz też  
 [DBViewer](../../visual-cpp-samples.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB — Kompendium szablonów konsumentów](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [Klasa CAccessor](../../data/oledb/caccessor-class.md)   
 [Cdynamicaccessor — klasa](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)