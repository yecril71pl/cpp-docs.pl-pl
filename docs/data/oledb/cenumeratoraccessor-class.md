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
- ATL::CEnumeratorAccessor::m_szDescription
- CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szDescription
- ATL.CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szName
- ATL.CEnumeratorAccessor.m_szName
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
ms.openlocfilehash: d85f630a01ab7e2a07035a8a304a56be91eca8a9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442004"
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor — Klasa

Używane przez [CEnumerator](../../data/oledb/cenumerator-class.md) do uzyskiwania dostępu do danych z zestawu wierszy modułu wyliczającego.

## <a name="syntax"></a>Składnia

```cpp
class CEnumeratorAccessor
```

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Elementy członkowskie

### <a name="data-members"></a>Elementy członkowskie danych

|||
|-|-|
|[m_bIsParent](#bisparent)|Zmienna wskazująca, czy moduł wyliczający jest nadrzędnym modułem wyliczania, jeśli wiersz jest modułem wyliczającym.|
|[m_nType](#ntype)|Zmienna wskazująca, czy w wierszu opisano źródło danych czy moduł wyliczający.|
|[m_szDescription](#szdescription)|Opis źródła danych lub modułu wyliczającego.|
|[m_szName](#szname)|Nazwa źródła danych lub modułu wyliczającego.|
|[m_szParseName](#szparsename)|Ciąg do przekazania do [IParseDisplayName](/windows/win32/api/oleidl/nn-oleidl-iparsedisplayname) w celu uzyskania monikera dla źródła danych lub modułu wyliczającego.|

## <a name="remarks"></a>Uwagi

Ten zestaw wierszy składa się ze źródeł danych i modułów wyliczających widocznych z bieżącego modułu wyliczającego.

## <a name="bisparent"></a>CEnumeratorAccessor:: m_bIsParent

Zmienna wskazująca, czy moduł wyliczający jest nadrzędnym modułem wyliczania, jeśli wiersz jest modułem wyliczającym.

### <a name="syntax"></a>Składnia

```cpp
VARIANT_BOOL m_bIsParent;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) w *dokumentacji programisty OLE DB* .

## <a name="ntype"></a>CEnumeratorAccessor:: m_nType

Zmienna wskazująca, czy w wierszu opisano źródło danych czy moduł wyliczający.

### <a name="syntax"></a>Składnia

```cpp
USHORT m_nType;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) w *dokumentacji programisty OLE DB* .

## <a name="szdescription"></a>CEnumeratorAccessor:: m_szDescription

Opis źródła danych lub modułu wyliczającego.

### <a name="syntax"></a>Składnia

```cpp
WCHAR m_szDescription[129];
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) w *dokumentacji programisty OLE DB* .

## <a name="szname"></a>CEnumeratorAccessor:: m_szName

Nazwa źródła danych lub modułu wyliczającego.

### <a name="syntax"></a>Składnia

```cpp
WCHAR m_szName[129];
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) w *dokumentacji programisty OLE DB* .

## <a name="szparsename"></a>CEnumeratorAccessor:: m_szParseName

Ciąg do przekazania do [IParseDisplayName](/windows/win32/api/oleidl/nn-oleidl-iparsedisplayname) w celu uzyskania monikera dla źródła danych lub modułu wyliczającego.

### <a name="syntax"></a>Składnia

```cpp
WCHAR m_szParseName[129];
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) w *dokumentacji programisty OLE DB* .

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)