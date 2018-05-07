---
title: Cdaoworkspaceinfo — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDaoWorkspaceInfo
dev_langs:
- C++
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd6979124916e8a9cc1dc723008491bababc0322
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo — Struktura
`CDaoWorkspaceInfo` Struktura zawiera informacje o zdefiniowanych dla dostępu do danych dostępu do obiektów (DAO) bazy danych obszaru roboczego.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CDaoWorkspaceInfo  
{  
    CString m_strName;           // Primary  
    CString m_strUserName;       // Secondary  
    BOOL m_bIsolateODBCTrans;    // All  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 `m_strName`  
 Unikatowej nazwy obiektu obszaru roboczego. Aby bezpośrednio pobrać wartości tej właściwości, należy wywołać obiekt querydef [GetName](../../mfc/reference/cdaoquerydef-class.md#getname) funkcję elementu członkowskiego. Aby uzyskać więcej informacji zobacz temat "Właściwości Name" w pomocy DAO.  
  
 *m_strUserName*  
 Wartość, która reprezentuje właścicielem obiektu obszaru roboczego. Powiązane informacje zobacz temat "Właściwości nazwy użytkownika" w pomocy DAO.  
  
 *m_bIsolateODBCTrans*  
 Wartość, która wskazuje, czy wiele transakcji, które dotyczą tej samej bazy danych ODBC są izolowane. Aby uzyskać więcej informacji, zobacz [CDaoWorkspace::SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans). Powiązane informacje zobacz temat "IsolateODBCTrans Property" w pomocy DAO.  
  
## <a name="remarks"></a>Uwagi  
 Obszar roboczy jest obiekt klasy [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Odwołania do podstawowej, pomocniczej i wszystkie powyższe wskazują, jak informacje zwracane przez [GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) funkcji członkowskiej klasy `CDaoWorkspace`.  
  
 Informacje o pobrane przez [CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) funkcja członkowska jest przechowywany w `CDaoWorkspaceInfo` struktury. `CDaoWorkspaceInfo` definiuje również `Dump` kompilacje funkcji członkowskiej podczas debugowania. Można użyć `Dump` do zrzutu zawartość `CDaoWorkspaceInfo` obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdao.h  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Klasa CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)
