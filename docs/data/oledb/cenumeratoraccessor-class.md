---
title: CEnumeratorAccessor — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
- CEnumeratorAccessor.m_bIsParent
- ATL::CEnumeratorAccessor::m_bIsParent
- m_bIsParent
- ATL.CEnumeratorAccessor.m_bIsParent
- CEnumeratorAccessor::m_bIsParent
- ATL::CEnumeratorAccessor::m_nType
- CEnumeratorAccessor.m_nType
- CEnumeratorAccessor::m_nType
- ATL.CEnumeratorAccessor.m_nType
- m_nType
- ATL::CEnumeratorAccessor::m_szDescription
- CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szDescription
- ATL.CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szName
- ATL.CEnumeratorAccessor.m_szName
- m_szName
- ATL::CEnumeratorAccessor::m_szName
- CEnumeratorAccessor.m_szName
- CEnumeratorAccessor::m_szParseName
- ATL::CEnumeratorAccessor::m_szParseName
- m_szParseName
- CEnumeratorAccessor.m_szParseName
- ATL.CEnumeratorAccessor.m_szParseName
helpviewer_keywords:
- CEnumeratorAccessor class
- m_bIsParent
- m_nType
- m_szDescription
- m_szName
- m_szParseName
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
ms.openlocfilehash: e609b346bb4a0c2469c24e20540c646fa869ae26
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025166"
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor — Klasa

Używane przez [CEnumerator](../../data/oledb/cenumerator-class.md) dostępu do danych z zestawu wierszy modułu wyliczającego.

## <a name="syntax"></a>Składnia

```cpp
class CEnumeratorAccessor
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="members"></a>Elementy członkowskie

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_bIsParent](#bisparent)|Zmienną określającą, czy moduł wyliczający jest wyliczający nadrzędnego, jeśli wiersz jest moduł wyliczający.|
|[m_nType](#ntype)|Zmienną określającą, czy wiersz zawiera opis źródła danych lub moduł wyliczający.|
|[m_szDescription](#szdescription)|Opis źródła danych lub modułu wyliczającego.|
|[m_szName](#szname)|Nazwa źródła danych lub modułu wyliczającego.|
|[m_szParseName](#szparsename)|Parametry do przekazania do [IParseDisplayName](/windows/desktop/api/oleidl/nn-oleidl-iparsedisplayname) uzyskać krótka nazwa dla źródła danych lub modułu wyliczającego.|

## <a name="remarks"></a>Uwagi

Ten zestaw wierszy składa się z źródła danych i moduły wyliczające widoczne z bieżącej modułu wyliczającego.

## <a name="bisparent"></a> CEnumeratorAccessor::m_bIsParent

Zmienną określającą, czy moduł wyliczający jest wyliczający nadrzędnego, jeśli wiersz jest moduł wyliczający.

### <a name="syntax"></a>Składnia

```cpp
VARIANT_BOOL m_bIsParent;
```

### <a name="remarks"></a>Uwagi

Zobacz [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji.

## <a name="ntype"></a> CEnumeratorAccessor::m_nType

Zmienną określającą, czy wiersz zawiera opis źródła danych lub moduł wyliczający.

### <a name="syntax"></a>Składnia

```cpp
USHORT m_nType;
```

### <a name="remarks"></a>Uwagi

Zobacz [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji.

## <a name="szdescription"></a> CEnumeratorAccessor::m_szDescription

Opis źródła danych lub modułu wyliczającego.

### <a name="syntax"></a>Składnia

```cpp
WCHAR m_szDescription[129];
```

### <a name="remarks"></a>Uwagi

Zobacz [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji.

## <a name="szname"></a> CEnumeratorAccessor::m_szName

Nazwa źródła danych lub modułu wyliczającego.

### <a name="syntax"></a>Składnia

```cpp
WCHAR m_szName[129];
```

### <a name="remarks"></a>Uwagi

Zobacz [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji.

## <a name="szparsename"></a> CEnumeratorAccessor::m_szParseName

Parametry do przekazania do [IParseDisplayName](/windows/desktop/api/oleidl/nn-oleidl-iparsedisplayname) uzyskać krótka nazwa dla źródła danych lub modułu wyliczającego.

### <a name="syntax"></a>Składnia

```cpp
WCHAR m_szParseName[129];
```

### <a name="remarks"></a>Uwagi

Zobacz [ISourcesRowset::GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) w *OLE DB Podręcznik programisty* Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)