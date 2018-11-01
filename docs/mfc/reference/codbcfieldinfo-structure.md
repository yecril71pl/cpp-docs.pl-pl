---
title: CODBCFieldInfo — Struktura
ms.date: 11/04/2016
f1_keywords:
- CODBCFieldInfo
helpviewer_keywords:
- ODBC [MFC], data source information
- CODBCFieldInfo structure [MFC]
ms.assetid: 92598b4f-facc-4108-b282-63a179ff79ab
ms.openlocfilehash: 5ad7d8f710c763b25771e3d1fa8839b5b64802ad
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655276"
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

