---
title: CODBCFieldInfo — Struktura
ms.date: 11/04/2016
f1_keywords:
- CODBCFieldInfo
helpviewer_keywords:
- ODBC [MFC], data source information
- CODBCFieldInfo structure [MFC]
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
ms.openlocfilehash: bc2ad0c8319a60b773211dbd6b52b57bb2dbcafb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272766"
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

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)<br/>
[CRecordset::GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)
