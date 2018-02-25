---
title: "Cdynamicparameteraccessor — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicParameterAccessor class
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 18f53ca6d95d215ad41c6b2501245be0e470bbb1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor — Klasa

Podobnie jak [cdynamicaccessor —](../../data/oledb/cdynamicaccessor-class.md) , ale uzyskuje informacje o parametrach określonych przez wywołanie [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) interfejsu.

## <a name="syntax"></a>Składnia

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="members"></a>Elementy członkowskie

### <a name="methods"></a>Metody

|||
|-|-|
|[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-cdynamicparameteraccessor.md)|Konstruktor.|
|[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)|Pobiera dane parametru z buforu.|
|[GetParamCount](../../data/oledb/cdynamicparameteraccessor-getparamcount.md)|Pobiera liczbę parametrów w metodzie dostępu.|
|[GetParamIO](../../data/oledb/cdynamicparameteraccessor-getparamio.md)|Określa, czy określony parametr jest parametrem wejściowych lub wyjściowych.|
|[GetParamLength](../../data/oledb/cdynamicparameteraccessor-getparamlength.md)|Pobiera długość określonego parametru przechowywane w buforze.|
|[GetParamName](../../data/oledb/cdynamicparameteraccessor-getparamname.md)|Pobiera nazwę określonego parametru.|
|[GetParamStatus](../../data/oledb/cdynamicparameteraccessor-getparamstatus.md)|Pobiera stan określony parametr przechowywane w buforze.|
|[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)|Pobiera dane ciągu określonego parametru przechowywane w buforze.|
|[GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)|Pobiera typ danych określony parametr.|
|[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)|Ustawia bufor przy użyciu danych parametru.|
|[SetParamLength](../../data/oledb/cdynamicparameteraccessor-setparamlength.md)|Ustawia długość określonego parametru przechowywane w buforze.|
|[SetParamStatus](../../data/oledb/cdynamicparameteraccessor-setparamstatus.md)|Ustawia stan określony parametr przechowywane w buforze.|
|[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)|Ustawia dane ciągu określonego parametru przechowywane w buforze.|

## <a name="remarks"></a>Uwagi

Dostawca musi obsługiwać `ICommandWithParameters` dla konsumentów użyć tej klasy.

Informacje o parametrach znajduje się w buforze tworzone i zarządzane przez tę klasę. Uzyskaj parametr danych z bufora za pomocą [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) i [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Na przykład pokazuje sposób użycia tej klasy wykonywanie procedury składowane programu SQL Server w celu uzyskania wartości parametrów wyjściowych, zobacz [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) przykładowy kod przedstawiony w [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) repozytorium w witrynie GitHub.

## <a name="requirements"></a>Wymagania

**Nagłówek**: atldbcli.h

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)  
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)  
[CAccessor, klasa](../../data/oledb/caccessor-class.md)  
[CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)  
[CManualAccessor, klasa](../../data/oledb/cmanualaccessor-class.md)  
