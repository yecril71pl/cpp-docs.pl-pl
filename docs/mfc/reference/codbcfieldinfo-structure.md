---
title: Codbcfieldinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CODBCFieldInfo
dev_langs:
- C++
helpviewer_keywords:
- ODBC [MFC], data source information
- CODBCFieldInfo structure [MFC]
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f178791bdaf57e5678f2e30d8994c2ffd140ffc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055800"
---
# <a name="codbcfieldinfo-structure"></a>CODBCFieldInfo — Struktura

`CODBCFieldInfo` Struktura zawiera informacje o polach w źródle danych ODBC.

## <a name="syntax"></a>Składnia

```
struct CODBCFieldInfo
{
    CString m_strName;
    SWORD m_nSQLType;
    UDWORD m_nPrecision;
    SWORD m_nScale;
    SWORD m_nNullability;
};
```

#### <a name="parameters"></a>Parametry

*m_strName*<br/>
Nazwa pola.

*m_nSQLType*<br/>
Typ danych SQL pola. Może to być typu danych ODBC SQL lub typ danych SQL specyficzne dla sterownika. Aby uzyskać listę prawidłowe typy danych ODBC SQL zobacz "Typy danych SQL" w zestawie Windows SDK. Aby uzyskać informacje o typach danych SQL specyficzne dla sterownika można znaleźć w temacie sterownika dokumentacji.

*m_nPrecision*<br/>
Maksymalna dokładność pola. Aby uzyskać szczegółowe informacje zobacz "Dokładność, skala, długość i rozmiar wyświetlania" w zestawie Windows SDK.

*m_nScale*<br/>
Skala pola. Aby uzyskać szczegółowe informacje zobacz "Dokładność, skala, długość i rozmiar wyświetlania" w zestawie Windows SDK.

*m_nNullability*<br/>
Czy pole akceptuje wartości Null. Może to być jeden z dwóch wartości: SQL_NULLABLE, jeśli pole akceptuje wartości Null lub SQL_NO_NULLS, jeśli pole nie akceptuje wartości Null.

## <a name="remarks"></a>Uwagi

Aby pobrać te informacje, należy wywołać [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdb.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)<br/>
[CRecordset::GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)

