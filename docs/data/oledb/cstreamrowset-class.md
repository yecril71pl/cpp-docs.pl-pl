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
dev_langs:
- C++
helpviewer_keywords:
- CStreamRowset class
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3365767ed36bcdc45e87f08fb038500fa9ac6d82
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100034"
---
# <a name="cstreamrowset-class"></a>CStreamRowset — Klasa
Używane w `CCommand` lub `CTable` deklaracji.  
  
## <a name="syntax"></a>Składnia

```cpp
template <class TAccessor = CAccessorBase>  
class CStreamRowset  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Klasa metody dostępu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CStreamRowset](../../data/oledb/cstreamrowset-cstreamrowset.md)|Konstruktor. Tworzy i inicjuje `CStreamRowset` obiektu.|  
|[Zamknij](../../data/oledb/cstreamrowset-close.md)|Wersje [ISequentialStream](https://msdn.microsoft.com/en-us/library/ms718035.aspx) wskaźnika interfejsu w klasie.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `CStreamRowset` w Twojej `CCommand` lub `CTable` deklaracji, na przykład:  
  
 [!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]  
  
 lub  
  
 [!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]  
  
 `ICommand::Execute` Zwraca `ISequentialStream` wskaźnika, który jest przechowywany w `m_spStream`. Następnie należy użyć **odczytu** metody do pobierania danych (ciąg Unicode) w formacie XML. Na przykład:  
  
 [!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]  
  
 SQL Server 2000 wykonuje formatowania XML i zwróci wszystkie kolumny i wszystkie wiersze z zestawu wierszy w postaci jednego ciągu XML.  
  
> [!NOTE]
>  Ta funkcja działa tylko z programem SQL Server 2000.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)