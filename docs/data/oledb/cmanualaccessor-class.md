---
title: CManualAccessor — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
helpviewer_keywords:
- CManualAccessor class
- AddBindEntry method
- AddParameterEntry method
- CreateAccessor method
- CreateParameterAccessor method
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
ms.openlocfilehash: 4d9fb79bbf5203fa959672faec8c3b076c17f1ca
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211851"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor — Klasa

Reprezentuje typ metody dostępu zaprojektowany do użycia zaawansowanego.

## <a name="syntax"></a>Składnia

```cpp
class CManualAccessor : public CAccessorBase
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Members

### <a name="methods"></a>Metody

|||
|-|-|
|[AddBindEntry](#addbindentry)|Dodaje wpis powiązania do kolumn danych wyjściowych.|
|[AddParameterEntry](#addparameterentry)|Dodaje wpis parametru do metody dostępu do parametru.|
|[CreateAccessor](#createaccessor)|Przydziela pamięć dla struktur powiązań kolumn i inicjuje elementy członkowskie danych kolumny.|
|[CreateParameterAccessor](#createparameteraccessor)|Przydziela pamięć dla struktur powiązań parametrów i inicjuje elementy członkowskie danych parametru.|

## <a name="remarks"></a>Uwagi

Za pomocą `CManualAccessor`można określić parametry i powiązania kolumn wyjściowych przez wywołania funkcji czasu wykonywania.

## <a name="cmanualaccessoraddbindentry"></a><a name="addbindentry"></a>CManualAccessor:: AddBindEntry

Dodaje wpis powiązania do kolumn danych wyjściowych.

### <a name="syntax"></a>Składnia

```cpp
void AddBindEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL) throw ();
```

#### <a name="parameters"></a>Parametry

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *dokumentacji programisty OLE DB*.

*nOrdinal*<br/>
podczas Numer kolumny.

*wType*<br/>
podczas Typ danych.

*nColumnSize*<br/>
podczas Rozmiar kolumny w bajtach.

*pData*<br/>
podczas Wskaźnik do danych kolumny przechowywanych w buforze.

*pLength*<br/>
podczas Wskaźnik do długości pola, jeśli jest to wymagane.

*pStatus*<br/>
podczas Wskaźnik do zmiennej, która ma zostać powiązana ze stanem kolumny, jeśli jest to wymagane.

### <a name="remarks"></a>Uwagi

Aby użyć tej funkcji, należy najpierw wywołać metodę [dostępu](../../data/oledb/cmanualaccessor-createaccessor.md). Nie można dodać więcej wpisów niż liczba kolumn określona w `CreateAccessor`.

## <a name="cmanualaccessoraddparameterentry"></a><a name="addparameterentry"></a>CManualAccessor:: AddParameterEntry

Dodaje wpis parametru do struktur wpisów parametrów.

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

Zobacz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) w *dokumentacji programisty OLE DB*.

*nOrdinal*<br/>
podczas Numer parametru.

*wType*<br/>
podczas Typ danych.

*nColumnSize*<br/>
podczas Rozmiar kolumny w bajtach.

*pData*<br/>
podczas Wskaźnik do danych kolumny przechowywanych w buforze.

*pLength*<br/>
podczas Wskaźnik do długości pola, jeśli jest to wymagane.

*pStatus*<br/>
podczas Wskaźnik do zmiennej, która ma zostać powiązana ze stanem kolumny, jeśli jest to wymagane.

*eParamIO*<br/>
podczas Określa, czy parametr, z którym jest skojarzone powiązanie, jest parametrem wejściowym, wejściowym/wyjściowym lub wyjściowym.

### <a name="remarks"></a>Uwagi

Aby użyć tej funkcji, należy najpierw wywołać [CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md).

## <a name="cmanualaccessorcreateaccessor"></a><a name="createaccessor"></a>CManualAccessor:: isdostępu

Przydziela pamięć dla struktur powiązań kolumn i inicjuje elementy członkowskie danych kolumny.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CreateAccessor(int nBindEntries,
  void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>Parametry

*nBindEntries*<br/>
podczas Liczba kolumn. Ta liczba powinna być zgodna z liczbą wywołań funkcji [CManualAccessor:: AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) .

*pBuffer*<br/>
podczas Wskaźnik do buforu, w którym są przechowywane kolumny wyjściowe.

*nBufferSize*<br/>
podczas Rozmiar buforu w bajtach.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję przed wywołaniem funkcji `CManualAccessor::AddBindEntry`.

## <a name="cmanualaccessorcreateparameteraccessor"></a><a name="createparameteraccessor"></a>CManualAccessor:: CreateParameterAccessor

Przydziela pamięć dla struktur powiązań parametrów i inicjuje elementy członkowskie danych parametru.

### <a name="syntax"></a>Składnia

```cpp
HRESULT CreateParameterAccessor(int nBindEntries,
   void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>Parametry

*nBindEntries*<br/>
podczas Liczba kolumn.

*pBuffer*<br/>
podczas Wskaźnik do buforu, w którym są przechowywane kolumny wejściowe.

*nBufferSize*<br/>
podczas Rozmiar buforu w bajtach.

### <a name="return-value"></a>Wartość zwracana

Jedna ze standardowych wartości HRESULT.

### <a name="remarks"></a>Uwagi

Przed wywołaniem [AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md)należy wywołać tę funkcję.

## <a name="see-also"></a>Zobacz też

[DBVIEWER](../../overview/visual-cpp-samples.md)<br/>
[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, klasa](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)
