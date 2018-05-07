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
ms.openlocfilehash: 88bcac3c7ce4658ec7dafeaa1cac45b5f2450298
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="codbcfieldinfo-structure"></a>CODBCFieldInfo — Struktura
`CODBCFieldInfo` Struktura zawiera informacje dotyczące pól w źródle danych ODBC.  
  
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
 `m_strName`  
 Nazwa pola.  
  
 *m_nSQLType*  
 Typ danych SQL pola. Może to być typ danych ODBC SQL lub sterownika typ danych SQL. Aby uzyskać listę prawidłowe typy danych ODBC SQL zobacz "Typy danych SQL" w zestawie Windows SDK. Informacje na temat typów danych SQL sterownika sterownika dokumentacji.  
  
 *m_nPrecision*  
 Maksymalna dokładność pola. Aby uzyskać więcej informacji zobacz "Precyzja, skala długość i rozmiar wyświetlania" w zestawie Windows SDK.  
  
 *m_nScale*  
 Skala pola. Aby uzyskać więcej informacji zobacz "Precyzja, skala długość i rozmiar wyświetlania" w zestawie Windows SDK.  
  
 *m_nNullability*  
 Określa, czy pole akceptuje wartości Null. Może to być jedną z dwóch wartości: **SQL_NULLABLE** Jeśli pole akceptuje wartości Null lub **SQL_NO_NULLS** Jeśli pole nie akceptuje wartości Null.  
  
## <a name="remarks"></a>Uwagi  
 Aby pobrać te informacje, należy wywołać [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRecordset::GetODBCFieldInfo](../../mfc/reference/crecordset-class.md#getodbcfieldinfo)   
 [CRecordset::GetFieldValue](../../mfc/reference/crecordset-class.md#getfieldvalue)


