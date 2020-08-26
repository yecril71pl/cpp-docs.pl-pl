---
title: CStreamRowset — Klasa
ms.date: 11/04/2016
f1_keywords:
- ATL::CStreamRowset<TAccessor>
- ATL::CStreamRowset
- CStreamRowset
- ATL.CStreamRowset<TAccessor>
- ATL.CStreamRowset
- CStreamRowset::CStreamRowset
- CStreamRowset.CStreamRowset
- ATL.CStreamRowset.CStreamRowset
- ATL::CStreamRowset::CStreamRowset
- CStreamRowset<TAccessor>::CStreamRowset
- ATL::CStreamRowset<TAccessor>::CStreamRowset
- CStreamRowset<TAccessor>.Close
- ATL.CStreamRowset<TAccessor>.Close
- CStreamRowset::Close
- CStreamRowset<TAccessor>::Close
- ATL::CStreamRowset::Close
- ATL.CStreamRowset.Close
- ATL::CStreamRowset<TAccessor>::Close
- CStreamRowset.Close
helpviewer_keywords:
- CStreamRowset class
- CStreamRowset class, constructor
- Close method
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
ms.openlocfilehash: 304dfe0e026a9fbba899c1ef17c06cf1baf1529b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841054"
---
# <a name="cstreamrowset-class"></a>CStreamRowset — Klasa

Używane w `CCommand` deklaracji lub `CTable` .

## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Klasa akcesora.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli. h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

| Nazwa | Opis |
|-|-|
|[CStreamRowset](#cstreamrowset)|Konstruktor. Tworzy wystąpienia i inicjuje `CStreamRowset` obiekt.|
|[Zamknij](#close)|Zwalnia wskaźnik interfejsu [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) w klasie.|

## <a name="remarks"></a>Uwagi

Użyj `CStreamRowset` w `CCommand` deklaracji lub `CTable` , na przykład:

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

lub

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute` zwraca `ISequentialStream` wskaźnik, który jest przechowywany w `m_spStream` . Następnie użyj metody, `Read` Aby pobrać dane (ciąg Unicode) w formacie XML. Na przykład:

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 wykonuje formatowanie XML i zwróci wszystkie kolumny i wszystkie wiersze zestawu wierszy jako jeden ciąg XML.

> [!NOTE]
> Ta funkcja działa tylko z SQL Server 2000.

## <a name="cstreamrowsetcstreamrowset"></a><a name="cstreamrowset"></a> CStreamRowset:: CStreamRowset

Tworzy wystąpienia i inicjuje `CStreamRowset` obiekt.

### <a name="syntax"></a>Składnia

```cpp
CStreamRowset();
```

## <a name="cstreamrowsetclose"></a><a name="close"></a> CStreamRowset:: Close

Zwalnia wskaźnik interfejsu [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) w klasie.

### <a name="syntax"></a>Składnia

```cpp
void Close();
```

## <a name="see-also"></a>Zobacz też

[OLE DB Szablony konsumentów](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów klientów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
