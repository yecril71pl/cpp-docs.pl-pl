---
title: Cdynamicstringaccessora — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessorA
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessorA class
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 612050c74cf33d128f108962fab54ef6c0e8e5d9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214568"
---
# <a name="cdynamicstringaccessora-class"></a>CDynamicStringAccessorA — Klasa

Umożliwia dostęp do źródła danych, gdy masz nie znajomości schematu bazy danych (wewnętrzna struktura).

## <a name="syntax"></a>Składnia

```cpp
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;
```

## <a name="remarks"></a>Uwagi

Oba żądania, że dostawca pobrać wszystkie dane używane z magazynu danych jako dane ciągu, ale `CDynamicStringAccessor` dane ciągowe żądań ANSI.

`CDynamicStringAccessorA` dziedziczy `GetString` i `SetString` z `CDynamicStringAccessor`. Jeśli używasz tych metod w `CDynamicStringAccessorA` obiektu `BaseType` jest **CHAR**.

## <a name="requirements"></a>Wymagania

**Nagłówek**: atldbcli.h

## <a name="see-also"></a>Zobacz też

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor, klasa](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor, klasa](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor, klasa](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor, klasa](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
