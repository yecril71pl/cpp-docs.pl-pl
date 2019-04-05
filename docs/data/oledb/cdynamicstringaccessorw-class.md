---
title: CDynamicStringAccessorW — Klasa
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessorW
helpviewer_keywords:
- CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
ms.openlocfilehash: 20ea4a2d795108e00c4b11c3abea6cf7b9953ca7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025153"
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

## <a name="see-also"></a>Zobacz także

[Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Szablony konsumentów OLE DB — kompendium](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Klasa CAccessor](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor — Klasa](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor — Klasa](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor — Klasa](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor — Klasa](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
