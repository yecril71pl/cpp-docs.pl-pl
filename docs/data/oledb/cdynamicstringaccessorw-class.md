---
title: CDynamicStringAccessorW — Klasa
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessorW
helpviewer_keywords:
- CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
ms.openlocfilehash: 7052a912363d1256294131da9b89df97f768ecf8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551362"
---
# <a name="cdynamicstringaccessorw-class"></a>CDynamicStringAccessorW — Klasa

Umożliwia dostęp do źródła danych, gdy masz nie znajomości schematu bazy danych (wewnętrzna struktura).

## <a name="syntax"></a>Składnia

```cpp
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;
```

## <a name="remarks"></a>Uwagi

Oba żądania, że dostawca pobrać wszystkie dane używane z magazynu danych jako dane ciągu, ale `CDynamicStringAccessor` żąda danych ciąg Unicode.

`CDynamicStringAccessorW` dziedziczy `GetString` i `SetString` z `CDynamicStringAccessor`. Jeśli używasz tych metod w `CDynamicStringAccessorW` obiektu `BaseType` jest **WCHAR**.

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
