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
ms.openlocfilehash: ad4987422fd200faef141150908d4df0722f669a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366272"
---
# <a name="cstreamrowset-class"></a>CStreamRowset — Klasa

Używane w `CCommand` `CTable` deklaracji lub.

## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
```

### <a name="parameters"></a>Parametry

*TAccessor ( TAccessor )*<br/>
Klasa akcesora.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atldbcli.h

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[Cstreamrowset](#cstreamrowset)|Konstruktor. Wystąpienia i inicjuje `CStreamRowset` obiekt.|
|[Zamknij](#close)|Zwalnia wskaźnik interfejsu [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) w klasie.|

## <a name="remarks"></a>Uwagi

Użyj `CStreamRowset` w `CCommand` `CTable` swoim lub deklaracji, na przykład:

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

lub

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute`zwraca `ISequentialStream` wskaźnik, który jest `m_spStream`przechowywany w pliku . Następnie należy `Read` użyć metody do pobrania danych (ciąg Unicode) w formacie XML. Przykład:

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

Program SQL Server 2000 wykonuje formatowanie XML i zwraca wszystkie kolumny i wszystkie wiersze zestawu wierszy jako jeden ciąg XML.

> [!NOTE]
> Ta funkcja działa tylko z programem SQL Server 2000.

## <a name="cstreamrowsetcstreamrowset"></a><a name="cstreamrowset"></a>CStreamRowset::CStreamRowset

Wystąpienia i inicjuje `CStreamRowset` obiekt.

### <a name="syntax"></a>Składnia

```cpp
CStreamRowset();
```

## <a name="cstreamrowsetclose"></a><a name="close"></a>CStreamRowset::Zamknij

Zwalnia wskaźnik interfejsu [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) w klasie.

### <a name="syntax"></a>Składnia

```cpp
void Close();
```

## <a name="see-also"></a>Zobacz też

[Szablony dla konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Dokumentacja szablonów dla konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
