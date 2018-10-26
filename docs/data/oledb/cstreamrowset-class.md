---
title: Cstreamrowset — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
- CStreamRowset
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
dev_langs:
- C++
helpviewer_keywords:
- CStreamRowset class
- CStreamRowset class, constructor
- Close method
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8a19085ae5d46396415e5b54b9acada547bc8079
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077793"
---
# <a name="cstreamrowset-class"></a>CStreamRowset — Klasa

Używane w `CCommand` lub `CTable` deklaracji.

## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
```

### <a name="parameters"></a>Parametry

*TAccessor*<br/>
Klasa metody dostępu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[CStreamRowset](#cstreamrowset)|Konstruktor. Tworzy i inicjuje `CStreamRowset` obiektu.|
|[Zamknij](#close)|Wersje [ISequentialStream](/previous-versions/windows/desktop/ms718035) wskaźnik interfejsu w klasie.|

## <a name="remarks"></a>Uwagi

Użyj `CStreamRowset` w swojej `CCommand` lub `CTable` deklaracji, na przykład:

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

lub

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute` Zwraca `ISequentialStream` wskaźnika, który jest przechowywany w `m_spStream`. Następnie użyj `Read` metody do pobierania danych (ciąg Unicode) w formacie XML. Na przykład:

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 wykonuje formatowania XML i zwróci wszystkie kolumny i wszystkie wiersze z wierszy jako jeden ciąg XML.

> [!NOTE]
>  Ta funkcja działa tylko z programem SQL Server 2000.

## <a name="cstreamrowset"></a> CStreamRowset::CStreamRowset

Tworzy i inicjuje `CStreamRowset` obiektu.

### <a name="syntax"></a>Składnia

```cpp
CStreamRowset();
```

## <a name="close"></a> CStreamRowset::Close

Wersje [ISequentialStream](/previous-versions/windows/desktop/ms718035) wskaźnik interfejsu w klasie.

### <a name="syntax"></a>Składnia

```cpp
void Close();
```

## <a name="see-also"></a>Zobacz też

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)